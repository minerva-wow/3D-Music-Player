# 3D Music Player

一个使用原生JavaScript开发的支持3D音频的Web音乐播放器。

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-1.0.0-green.svg)

## 功能特点

- 🎧 3D空间音频效果
- 🎼 实时音频可视化
- 📱 响应式设计
- 🎵 歌词同步显示
- 📝 播放列表管理
- ❤️ 收藏夹功能
- 💾 本地数据存储
- 🎨 可自定义主题

## 技术栈

- 原生JavaScript (ES6+)
- Web Audio API
- Canvas API
- CSS3 动画
- localStorage
- Webpack
- Jest (单元测试)

## 项目结构

```
3d-music-player/
├── src/
│   ├── js/
│   │   ├── core/
│   │   │   ├── AudioEngine.js
│   │   │   ├── PlaylistManager.js
│   │   │   └── StorageManager.js
│   │   ├── ui/
│   │   │   ├── Visualizer.js
│   │   │   ├── Controls.js
│   │   │   └── LyricsDisplay.js
│   │   └── utils/
│   │       ├── AudioHelper.js
│   │       └── DOMHelper.js
│   ├── css/
│   │   ├── main.css
│   │   ├── player.css
│   │   └── themes/
│   │       ├── default.css
│   │       └── dark.css
│   └── assets/
│       ├── icons/
│       └── demo-songs/
├── dist/
├── tests/
├── docs/
├── webpack.config.js
├── package.json
└── README.md
```

## 安装

1. 克隆仓库：
```bash
git clone https://github.com/minerva-wow/3D-Music-Player.git
cd 3d-music-player
```

2. 安装依赖：
```bash
npm install
```

3. 启动开发服务器：
```bash
npm run dev
```

4. 构建生产版本：
```bash
npm run build
```

## 使用方法

### 基础使用

```javascript
// 创建播放器实例
const player = new MusicPlayer({
  container: document.getElementById('player-container'),
  theme: 'default'
});

// 加载音乐
player.loadTrack({
  url: 'path/to/music.mp3',
  title: '歌曲名称',
  artist: '艺术家',
  lyrics: 'path/to/lyrics.lrc'
});

// 播放控制
player.play();
player.pause();
player.stop();
```

### 3D音频控制

```javascript
// 设置音源位置
player.setPosition(x, y, z);

// 应用预设效果
player.applyPreset('concert-hall');

// 自定义音频参数
player.setAudioParams({
  reverb: 0.5,
  roomSize: 0.8,
  distance: 1
});
```

## API文档

### MusicPlayer 类

#### 构造函数

```javascript
new MusicPlayer(options)
```

参数:
- `options.container` - DOM元素，播放器容器
- `options.theme` - 字符串，主题名称 (可选)
- `options.autoplay` - 布尔值，是否自动播放 (可选)

#### 方法

##### 核心功能

- `loadTrack(trackInfo)` - 加载音轨
- `play()` - 播放
- `pause()` - 暂停
- `stop()` - 停止
- `seek(time)` - 跳转到指定时间
- `setVolume(level)` - 设置音量

##### 3D音频控制

- `setPosition(x, y, z)` - 设置音源位置
- `setOrientation(x, y, z)` - 设置音源朝向
- `setListenerPosition(x, y, z)` - 设置听众位置
- `applyPreset(presetName)` - 应用预设效果

##### 播放列表管理

- `addToPlaylist(track)` - 添加到播放列表
- `removeFromPlaylist(trackId)` - 从播放列表移除
- `clearPlaylist()` - 清空播放列表
- `shufflePlaylist()` - 随机播放列表

##### 收藏夹功能

- `toggleFavorite(trackId)` - 切换收藏状态
- `getFavorites()` - 获取收藏列表
- `clearFavorites()` - 清空收藏列表

### 事件

```javascript
player.on('play', () => {
  console.log('开始播放');
});

player.on('pause', () => {
  console.log('暂停播放');
});

player.on('timeupdate', (currentTime) => {
  console.log('当前时间：', currentTime);
});

player.on('ended', () => {
  console.log('播放结束');
});
```

## 开发指南

### 环境要求

- Node.js >= 14.0.0
- npm >= 6.0.0
- 现代浏览器支持 (Chrome >= 64, Firefox >= 63, Safari >= 12)

### 开发流程

1. Fork 项目
2. 创建特性分支：`git checkout -b feature/your-feature-name`
3. 提交更改：`git commit -am 'Add some feature'`
4. 推送到分支：`git push origin feature/your-feature-name`
5. 提交 Pull Request

### 代码规范

- 使用 ESLint 进行代码检查
- 遵循 Airbnb JavaScript Style Guide
- 使用 Prettier 进行代码格式化
- 每个功能都需要编写测试用例

### 测试

```bash
# 运行所有测试
npm test

# 运行特定测试
npm test -- --grep "test name"

# 生成测试覆盖率报告
npm run test:coverage
```

## 关于作者

- GitHub: https://github.com/minerva-wow
- Email: andrea.b1062@gmail.com

## 常见问题

### Q: 如何处理跨域资源问题？
A: 在开发环境中使用 webpack-dev-server 的代理功能，或在生产环境中配置适当的 CORS 头。

### Q: 如何优化大型播放列表的性能？
A: 使用虚拟滚动技术，只渲染可视区域内的项目。

### Q: 如何处理不同音频格式的兼容性？
A: 使用 Audio Context 的 decodeAudioData 方法，并提供多种格式的音频源。