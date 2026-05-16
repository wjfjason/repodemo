# 贪吃蛇游戏 - 技术架构文档

## 1. 架构设计

```
┌─────────────────────────────────────────┐
│              前端层 (Frontend)           │
│  HTML5 + CSS3 + Vanilla JavaScript       │
│  ├── 游戏逻辑 (Game Logic)              │
│  ├── 渲染系统 (Canvas Renderer)         │
│  └── 用户输入处理 (Input Handler)       │
└─────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────┐
│              数据层 (Data Layer)         │
│  localStorage - 持久化存储最高分          │
└─────────────────────────────────────────┘
```

## 2. 技术栈

- **前端框架**：原生 HTML5 + CSS3 + JavaScript
- **渲染技术**：HTML5 Canvas API
- **动画引擎**：requestAnimationFrame
- **存储**：浏览器 localStorage
- **无外部依赖**：完全独立运行

## 3. 核心模块

| 模块 | 职责 |
|------|------|
| Game | 游戏主控制器，管理游戏状态和循环 |
| Snake | 蛇的数据结构和移动逻辑 |
| Food | 食物生成和位置管理 |
| Renderer | Canvas 渲染引擎 |
| InputHandler | 键盘和触摸输入处理 |
| ScoreManager | 分数计算和本地存储管理 |
| UI | 用户界面状态切换和显示 |

## 4. 游戏配置参数

| 参数 | 值 | 描述 |
|------|-----|------|
| CANVAS_SIZE | 400 | 游戏画布像素大小 |
| GRID_SIZE | 20 | 网格单元格数量 |
| CELL_SIZE | 20 | 每个单元格像素大小 |
| GAME_SPEED | 100 | 蛇移动间隔（毫秒） |
| INITIAL_LENGTH | 3 | 初始蛇身长度 |
| POINTS_PER_FOOD | 10 | 每个食物得分 |

## 5. 游戏状态机

```
START → (空格/点击) → PLAYING
PLAYING → (P键) → PAUSED
PAUSED → (P键) → PLAYING
PLAYING → (撞墙/撞身) → GAME_OVER
GAME_OVER → (空格/点击) → START
```

## 6. 文件结构

```
/workspace/
└── index.html  (单文件包含所有代码)
```

## 7. 性能优化

- 使用 requestAnimationFrame 确保流畅渲染
- 蛇身数据使用数组存储，shift/push 操作
- 碰撞检测使用空间坐标比较，O(n) 复杂度
- 游戏循环与渲染分离，提高响应性
