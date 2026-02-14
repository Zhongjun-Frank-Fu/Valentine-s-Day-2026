# Valentine Envelope — 上线 & 修改攻略

---

## 一、GitHub Pages 上线（5 分钟）

### 1. 新建仓库

- 打开 https://github.com/new
- Repository name 填 `valentine`（或任意名字）
- 选 **Public**
- 不勾 README，直接 **Create repository**

### 2. 上传文件

在仓库页面点 **uploading an existing file**，把 `valentine-preview.html` 重命名为 `index.html` 后拖进去。

> 因为是单文件版本，只需要这一个文件。

点 **Commit changes**。

### 3. 开启 Pages

- 进仓库 → **Settings** → 左侧 **Pages**
- Source 选 **Deploy from a branch**
- Branch 选 `main`，文件夹选 `/ (root)`
- 点 **Save**

### 4. 拿到链接

等 1-2 分钟，页面顶部会出现：

```
Your site is live at https://你的用户名.github.io/valentine/
```

这个链接就可以直接发给对方了。

---

## 二、修改攻略（直接改 HTML）

因为是单文件，所有内容都在 `index.html` 里。在 GitHub 仓库里点击文件 → 铅笔图标即可在线编辑。

### 改信封封面

搜索 `Happy Valentine's Day`，改成你想要的标题：

```html
<p class="envelope-title">你的标题</p>
<p class="envelope-to">To: 收件人名字</p>
```

### 改信纸正文

搜索 `Dear You,`，修改标题和正文：

```html
<h2 class="letter-heading">你的称呼,</h2>
<div class="letter-body">你的正文内容

支持换行，空一行就是段落间距。</div>
```

### 改两个选项的文字

搜索 `btnAccept`：

```html
<a class="choice-link" id="btnAccept" href="javascript:void(0)">接受</a>
<a class="choice-link" id="btnDecline" href="javascript:void(0)">再想想</a>
```

### 改点击后的感谢语

搜索 `Thank you` 和 `谢谢你打开这个网站`：

```javascript
showThank('Thank you');        // ← 点「接受」后显示
showThank('谢谢你打开这个网站');  // ← 点「再想想」后显示
```

### 改背景颜色

搜索 `background: linear-gradient(160deg`：

```css
background: linear-gradient(160deg, #fce4ec 0%, #f8bbd0 35%, #f48fb1 65%, #f06292 100%);
```

四个色值从浅到深，都是粉色系。换色直接替换 hex 值。

### 改信封颜色

搜索 `:root` 里的变量：

```css
--primary-pink: #e8829b;   /* 信封主色 */
--dark-pink: #c4546e;      /* 信封深色 / 选项文字色 */
--paper-color: #fffaf5;    /* 信纸背景 */
--text-color: #5d4037;     /* 正文文字色 */
```

---

## 三、常见问题

**Q: 改完怎么生效？**
在 GitHub 上编辑后点 Commit changes，等 1 分钟左右自动部署。

**Q: 想加背景音乐？**
在 `<body>` 结尾前加一个 `<audio>` 标签，然后在 `handleClick` 函数里的 `wrapper.classList.add('opening')` 后面加一行播放：

```html
<audio id="bgm" src="你的音乐链接.mp3" loop></audio>
```

```javascript
document.getElementById('bgm').play();
```

注意：音乐文件需要是公开可访问的 URL（可以传到仓库的 `assets/` 文件夹里）。

**Q: 想用自定义域名？**
Settings → Pages → Custom domain，填入你的域名，再去域名商配一条 CNAME 记录指向 `你的用户名.github.io`。
