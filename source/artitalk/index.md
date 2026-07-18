---
seo_title: 碎碎念
comments: false
---

<div id="supabase-artitalk">
  <div class="auth-section">
    <div id="login-form">
      <h3>登录发布说说</h3>
      <input type="email" id="email" placeholder="邮箱" />
      <input type="password" id="password" placeholder="密码" />
      <button id="login-btn">登录</button>
      <button id="register-btn">注册</button>
      <button id="reset-pwd-btn">忘记密码</button>
    </div>
    <div id="user-info" style="display: none;">
      <span id="user-email"></span>
      <button id="logout-btn">退出登录</button>
    </div>
  </div>

  <div id="post-section" style="display: none;">
    <textarea id="post-content" placeholder="絮絮叨叨絮絮叨···＞﹏＜···"></textarea>
    <button id="submit-btn">发布说说</button>
  </div>

  <div id="posts-container"></div>
</div>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<script>
const supabaseUrl = 'https://vsixpwyvpybuscxoogqq.supabase.co';
const supabaseKey = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZzaXhwd3l2cHlidXNjeG9vZ3FxIiwicm9sZSI6ImFub24iLCJpYXQiOjE3ODQyMzU3ODMsImV4cCI6MjA5OTgxMTc4M30.fjVqrkc1clVRzUBYNdeAYCPwuIY3TQmajhh169Q_ehM';
const supabase = supabase.createClient(supabaseUrl, supabaseKey);

const loginForm = document.getElementById('login-form');
const userInfo = document.getElementById('user-info');
const postSection = document.getElementById('post-section');
const postsContainer = document.getElementById('posts-container');

async function checkAuth() {
  const { data: { session } } = await supabase.auth.getSession();
  if (session) {
    document.getElementById('user-email').textContent = session.user.email;
    loginForm.style.display = 'none';
    userInfo.style.display = 'block';
    postSection.style.display = 'block';
  } else {
    loginForm.style.display = 'block';
    userInfo.style.display = 'none';
    postSection.style.display = 'none';
  }
}

document.getElementById('login-btn').addEventListener('click', async () => {
  const email = document.getElementById('email').value;
  const password = document.getElementById('password').value;
  const { error } = await supabase.auth.signInWithPassword({ email, password });
  if (error) alert('登录失败: ' + error.message);
  else checkAuth();
});

document.getElementById('register-btn').addEventListener('click', async () => {
  const email = document.getElementById('email').value;
  const password = document.getElementById('password').value;
  const { error } = await supabase.auth.signUp({ email, password });
  if (error) alert('注册失败: ' + error.message);
  else alert('注册成功，请登录');
});

document.getElementById('reset-pwd-btn').addEventListener('click', async () => {
  const email = document.getElementById('email').value;
  const { error } = await supabase.auth.resetPasswordForEmail(email);
  if (error) alert('重置失败: ' + error.message);
  else alert('重置链接已发送到邮箱');
});

document.getElementById('logout-btn').addEventListener('click', async () => {
  await supabase.auth.signOut();
  checkAuth();
});

document.getElementById('submit-btn').addEventListener('click', async () => {
  const content = document.getElementById('post-content').value;
  if (!content.trim()) return;
  const { data: { session } } = await supabase.auth.getSession();
  const { error } = await supabase.from('shuoshuo').insert({
    content,
    user_id: session.user.id,
    likes: 0,
    comments: 0,
    isShow: true
  });
  if (error) alert('发布失败: ' + error.message);
  else {
    document.getElementById('post-content').value = '';
    loadPosts();
  }
});

async function loadPosts() {
  const { data, error } = await supabase
    .from('shuoshuo')
    .select('*')
    .order('created_at', { ascending: false });
  if (error) {
    console.error('加载失败:', error);
    return;
  }
  postsContainer.innerHTML = data.map(post => `
    <div class="post-item">
      <p>${post.content}</p>
      <div class="post-meta">
        <span>${new Date(post.created_at).toLocaleString()}</span>
        <span>👍 ${post.likes || 0}</span>
        <span>💬 ${post.comments || 0}</span>
      </div>
    </div>
  `).join('');
}

checkAuth();
loadPosts();
</script>

<style>
#supabase-artitalk {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
.auth-section {
  margin-bottom: 20px;
  padding: 15px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
.auth-section input {
  display: block;
  width: 100%;
  padding: 10px;
  margin: 8px 0;
  border: 1px solid #ddd;
  border-radius: 4px;
}
.auth-section button {
  margin-right: 10px;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background: #44D7B6;
  color: #fff;
  cursor: pointer;
}
.auth-section button:hover {
  background: #38c4a3;
}
#post-section {
  margin-bottom: 20px;
  padding: 15px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
#post-section textarea {
  width: 100%;
  height: 100px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  resize: vertical;
}
#post-section button {
  margin-top: 10px;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background: #44D7B6;
  color: #fff;
  cursor: pointer;
}
#post-section button:hover {
  background: #38c4a3;
}
.post-item {
  margin-bottom: 15px;
  padding: 15px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
.post-item p {
  margin: 0 0 10px 0;
  line-height: 1.6;
}
.post-meta {
  font-size: 12px;
  color: #888;
}
.post-meta span {
  margin-right: 15px;
}
</style>