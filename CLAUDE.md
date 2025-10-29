# CLAUDE.md - PicHub 项目开发准则

## 📋 项目概览

**项目名称**: PicHub - 专业图床服务平台
**技术栈**: Laravel 11 + Blade + Tailwind CSS + Alpine.js
**数据库**: MySQL
**语言支持**: 中文、英文、法语、俄语

## 📝 README.md 规范

### Logo 图片规则
- **Logo 文件位置**: `/root/README.mini.png`
- **项目中路径**: `./public/images/pichub-logo.png`
- **README 中引用**: `<img src="./public/images/pichub-logo.png" alt="PicHub Logo" width="400">`
- **重要**: 更新 README.md 时必须使用 `/root/README.mini.png` 作为 Logo 源文件

### 内容规范
- **标题格式**: 不使用 emoji 图标，使用纯文本标题（如 `## 核心功能` 而非 `## ✨ 核心功能`）
- **简介部分**: 保持简洁，避免冗长描述
- **链接格式**: 使用 `[文本](链接)` 格式，不添加 emoji
- **GitHub 用户名**: 所有 GitHub 链接使用 `truman-world`，如 `https://github.com/truman-world/PicHub`

### Git 提交规范
- **用户名**: truman-world
- **邮箱**: truman-world@users.noreply.github.com
- **提交信息**: 不包含任何 Claude 相关信息
- **Co-Authored-By**: 不添加 Claude 作为共同作者

## 🌐 语言使用强制规范

⚠️ **绝对强制使用简体中文**

所有以下场景必须强制使用简体中文，无任何例外：
- ✅ AI 与用户的所有对话回复
- ✅ 所有文档（设计文档、API 文档、README 等）
- ✅ 所有代码注释（单行注释、多行注释、文档注释）
- ✅ Git 提交信息（commit message）
- ✅ 操作日志和任务描述
- ✅ 错误提示与警告信息

**唯一例外**: 代码标识符（变量名、函数名、类名）遵循项目既有命名约定（通常使用英文）。

## 🔍 编码前强制上下文检索清单（7步必查）

### 📊 任务复杂度分级

在开始检索前，先评估任务复杂度：

- **简单任务**（单文件、<50行、无依赖）：执行步骤1-3，简化验证
- **中等任务**（多文件、<200行、少量依赖）：执行完整7步，标准验证
- **复杂任务**（架构级、>200行、复杂依赖）：执行完整7步+增强验证

### ✅ 完整检索清单

#### □ 步骤1：文件名搜索（必须）

使用 Glob 工具搜索相关文件：

```bash
# 搜索相关 Blade 模板
Glob pattern="**/*关键词*.blade.php"

# 搜索相关控制器
Glob pattern="**/Http/Controllers/*关键词*.php"

# 搜索相关模型
Glob pattern="**/Models/*关键词*.php"

# 搜索组件
Glob pattern="**/components/*关键词*.blade.php"
```

**目标**: 找到5-10个候选文件
**记录**: 找到X个相关文件，重点关注 [列出文件路径]

#### □ 步骤2：内容搜索（必须）

使用 Grep 工具搜索关键实现：

```bash
# 搜索函数/方法实现
Grep pattern="function 函数名" output_mode="files_with_matches"
Grep pattern="public function|protected function" output_mode="content" -n=true

# 搜索 Blade 组件
Grep pattern="@component|x-|@include" output_mode="content"

# 搜索 Alpine.js 交互
Grep pattern="x-data|x-show|x-if|@click" output_mode="content"

# 搜索国际化键
Grep pattern="__\('messages\." output_mode="content"
```

**目标**: 找到关键实现位置
**记录**: 找到X处实现，重点分析 [file:line, file:line]

#### □ 步骤3：阅读相似实现（必须≥3个）

使用 Read 工具深度阅读至少3个相关文件：

```bash
Read file_path="/www/wwwroot/pichub.app/resources/views/components/xxx.blade.php"
Read file_path="/www/wwwroot/pichub.app/app/Http/Controllers/XxxController.php"
Read file_path="/www/wwwroot/pichub.app/app/Models/Xxx.php"
```

**关注点**:
- Laravel 路由和控制器模式
- Blade 模板组件复用方式
- Tailwind CSS 样式模式（响应式、深色模式）
- Alpine.js 交互模式（x-data、x-show、@click）
- 国际化 `__('messages.key')` 使用方式
- 错误处理和验证逻辑

**记录**: 分析了 [file1:line, file2:line, file3:line]，发现以下模式：[具体模式描述]

#### □ 步骤4：开源实现搜索（通用功能时可选）

针对通用功能（如算法、数据结构、设计模式），搜索开源实现学习最佳实践。

**触发条件**: 实现通用算法、复杂交互、性能优化等

#### □ 步骤5：国际化文件检查（涉及文本时必做）

检查所有4个语言文件：

```bash
Read file_path="/www/wwwroot/pichub.app/resources/lang/zh_CN/messages.php"
Read file_path="/www/wwwroot/pichub.app/resources/lang/en/messages.php"
Read file_path="/www/wwwroot/pichub.app/resources/lang/fr/messages.php"
Read file_path="/www/wwwroot/pichub.app/resources/lang/ru/messages.php"
```

**关注点**:
- 现有键名的命名模式
- 文本长度问题（法语、俄语通常更长）
- 是否需要添加新的翻译键

#### □ 步骤6：样式和布局模式分析（涉及UI时必做）

分析现有实现的样式模式：

- Tailwind 类的使用模式（utility-first）
- 响应式设计模式（sm:、md:、lg:、xl:）
- 深色模式模式（dark: 前缀）
- 布局方式（flex、grid、absolute/relative）
- 动画和过渡效果（transition-、duration-、ease-）

**记录**: 项目样式约定是 [具体描述]

#### □ 步骤7：模式提取和分析（必须）

使用 sequential-thinking 工具分析检索结果，生成项目模式清单：

```markdown
- 项目约定：命名规范、文件组织、导入顺序
- 可复用组件：[组件路径列表]
- 技术选型：为什么用这个方案？有何优缺点？
- 风险点：并发、边界、性能、安全
```

生成上下文摘要文件：`.claude/context-summary-[任务名].md`

## ✅ 上下文充分性验证（编码前最后关卡）

**必须全部回答"是"且提供具体证据，否则禁止进入编码阶段。**

### □ 1. 我能说出至少3个相似实现的文件路径吗？

- ✅ 是：[file1:line, file2:line, file3:line]
- ❌ 否 → 返回步骤1重新搜索

### □ 2. 我理解项目中这类功能的实现模式吗？

- ✅ 是：模式是 [Laravel路由→控制器→Blade模板→组件]，具体是 [详细描述]
- ❌ 不确定 → 返回步骤3深度阅读

### □ 3. 我知道项目中有哪些可复用的 Blade 组件吗？

- ✅ 是：在 resources/views/components/ 下有 [列出具体组件名和用途]
- ❌ 不知道 → 强制搜索 components 目录

### □ 4. 我理解项目的国际化模式吗？

- ✅ 是：使用 `__('messages.key')` 并在4个语言文件（zh_CN、en、fr、ru）中定义
- ❌ 不清楚 → 阅读 resources/lang/ 目录

### □ 5. 我理解项目的样式约定吗？

- ✅ 是：Tailwind CSS + 响应式（sm:/md:/lg:）+ 深色模式（dark:）
- ❌ 不清楚 → 分析现有组件的 class 属性

### □ 6. 我确认没有重复造轮子吗？

- ✅ 是：检查了 [具体模块/文件]，确认不存在相同功能
- ❌ 不确定 → 扩大搜索范围，检查 components/ 和 helpers/

### □ 7. 我知道如何清除缓存和验证修改吗？

- ✅ 是：`php artisan view:clear && php artisan view:cache`，然后测试所有语言和主题
- ❌ 不知道 → 学习 Laravel 缓存机制

## 📄 上下文摘要文件（编码前必须生成）

**路径**: `.claude/context-summary-[任务名].md`

**模板**:

```markdown
## PicHub 项目上下文摘要（[任务名称]）
生成时间：[YYYY-MM-DD HH:mm:ss]

### 1. 相似实现分析

- **实现1**: resources/views/components/xxx.blade.php:10-50
  - 模式：[Blade 组件 + Alpine.js]
  - 可复用：[具体组件]
  - Tailwind 样式：[class 模式]
  - 需注意：[响应式/深色模式/国际化]

- **实现2**: app/Http/Controllers/XxxController.php:30-80
  - 模式：[RESTful 控制器]
  - 可复用：[具体方法]
  - 需注意：[验证/授权/错误处理]

- **实现3**: resources/views/xxx/index.blade.php:100-150
  - 模式：[Blade 模板 + 组件组合]
  - 可复用：[布局/组件]
  - 需注意：[分页/排序/筛选]

### 2. Laravel 项目约定

- **路由定义**: routes/web.php（RESTful 风格）
- **控制器位置**: app/Http/Controllers/
- **控制器方法**: index、show、create、store、edit、update、destroy
- **Blade 模板**: resources/views/
- **Blade 组件**: resources/views/components/
- **模型**: app/Models/（使用 Eloquent ORM）
- **中间件**: app/Http/Middleware/
- **请求验证**: app/Http/Requests/

### 3. 可复用 Blade 组件清单

- `<x-safe-image>`: 安全图片组件，支持 fallback
- `<x-language-switcher>`: 桌面端语言切换组件
- `<x-mobile-language-switcher>`: 移动端语言切换组件
- `<x-simple-theme-toggle>`: 桌面端主题切换组件
- `<x-mobile-theme-toggle>`: 移动端主题切换组件
- `@include('components.tailwind-nav')`: 导航栏组件

### 4. 国际化策略

- **翻译函数**: `__('messages.key')` 或 `__('messages.section.key')`
- **语言文件**: resources/lang/{zh_CN,en,fr,ru}/messages.php
- **键名约定**: 小写+下划线，分层组织（如 `navigation.home`、`profile.edit`）
- **文本长度**: 法语、俄语文本通常比中英文长20-30%，需考虑布局
- **必须同步**: 添加新键时必须在所有4个语言文件中定义

### 5. 样式和交互模式

**Tailwind CSS 约定**:
- 响应式优先：移动端 → sm: → md: → lg: → xl:
- 深色模式：所有颜色类必须有 dark: 变体
- 避免内联 style，优先使用 Tailwind 类
- 复杂样式使用 `<style>` 标签，添加唯一 ID（如 `id="profile-styles-v3"`）

**Alpine.js 交互模式**:
- 使用 `x-data` 初始化组件状态
- 使用 `x-show`/`x-if` 控制显示
- 使用 `@click`/`@change` 绑定事件
- 使用 `x-transition` 添加过渡效果
- 避免复杂逻辑，必要时抽取到 `<script>` 中

**常见布局模式**:
- 导航栏：`flex items-center justify-between`
- 卡片：`rounded-lg shadow-md bg-white dark:bg-gray-800`
- 按钮：`px-3 py-2 rounded-md transition-all duration-300 hover:scale-105`
- 表单：`space-y-4` + 表单元素统一样式

### 6. 依赖和集成点

- **外部依赖**: Laravel 11、Tailwind CSS、Alpine.js
- **内部依赖**: [模块间依赖关系]
- **配置来源**: .env 文件、config/ 目录
- **缓存机制**: 视图缓存、配置缓存、路由缓存

### 7. 关键风险点

- **并发问题**: [潜在的竞态条件]
- **边界条件**: [需要处理的边界情况]
- **性能瓶颈**: [可能的性能问题]
- **缓存失效**: Blade 模板修改后必须清除缓存
- **国际化遗漏**: 新文本必须在所有4个语言文件中定义
```

## 🚨 懒惰检测与防护机制

### 核心原则

**研究先于编码，复用优于创造，一致性优于个人偏好。**

### 检测点1：编码前检测（Write/Edit 工具使用前）

**必须在开始编码前确认以下检查（记录在脑海中或注释中）**：

```markdown
□ 已查阅上下文摘要文件：.claude/context-summary-[任务名].md
□ 将复用以下 Blade 组件：
  - [组件1]: [路径] - [用途]
  - [组件2]: [路径] - [用途]
□ 将使用以下 Tailwind 类模式：[具体说明]
□ 将添加以下国际化键：[列出键名]
□ 确认不重复造轮子，证明：[说明检查了哪些模块]
```

**无法回答任何一项 → 立即终止，返回检索阶段。**

### 检测点2：编码中监控（每完成一个函数/类/模块）

对比上下文摘要，自查：

```markdown
□ 是否使用了摘要中列出的可复用组件？
  ✅ 是：已使用 [列出]
  ❌ 否：为什么不用？[合理解释]

□ 命名是否符合项目约定？
  ✅ 是：对比 [具体例子]
  ❌ 否：为什么偏离？[合理解释]

□ 样式是否一致（Tailwind + 响应式 + 深色模式）？
  ✅ 是：对比 [具体例子]
  ❌ 否：为什么偏离？[合理解释]

□ 是否添加了国际化支持？
  ✅ 是：已在4个语言文件中定义
  ❌ 否：立即补充
```

**"否"的数量超过50% → 触发 Level 1 警告。**

### 检测点3：编码后验证（功能实现完成后）

完整自检声明：

```markdown
## 编码后声明 - [功能名称]

### 1. 复用了以下既有组件
- [组件1]: 用于 [用途]，位于 [路径]
- [组件2]: 用于 [用途]，位于 [路径]

### 2. 遵循了以下项目约定
- 命名约定：[对比说明]
- 样式约定：[Tailwind + 响应式 + 深色模式]
- 国际化：[已在4个语言文件中定义]

### 3. 对比了以下相似实现
- [实现1]: 我的方案与其差异是 [具体差异]，理由是 [合理性说明]

### 4. 未重复造轮子的证明
- 检查了 [模块/文件列表]，确认不存在相同功能
```

**无法提供完整声明 → 视为懒惰，触发审查。**

### 三级惩罚体系

**Level 1 - 警告（首次检测到懒惰）**
1. 立即暂停编码
2. 要求立即修正偏离部分
3. 重新对比上下文摘要
4. 通过复查后继续编码

**Level 2 - 强制退回（二次检测到懒惰）**
1. 删除已编写的代码
2. 强制返回检索阶段
3. 重新生成上下文摘要
4. 重新通过充分性验证

**Level 3 - 任务失败（三次检测到懒惰）**
1. 标记任务为"失败"
2. 需要用户介入重新评估任务

## 💻 代码质量强制标准

### 📝 Blade 模板规范

**基本语法**:
- 使用 `@` 指令（@if、@foreach、@for、@while、@switch）
- 条件渲染：`@if`、`@elseif`、`@else`、`@endif`
- 循环：`@foreach`、`@endforeach`
- 注释：`{{-- 注释内容 --}}`
- 输出：`{{ $variable }}` 自动转义，`{!! $html !!}` 不转义

**组件复用**:
- 优先使用 `<x-component-name>` 组件语法
- 传递属性：`<x-alert type="error" :message="$message">`
- Slot 内容：`<x-card><x-slot name="header">标题</x-slot></x-card>`
- 包含子视图：`@include('components.xxx')`

**代码风格**:
- 保持缩进一致（通常4空格）
- 避免过深嵌套（最多3-4层）
- 长属性换行对齐

### 🎨 Tailwind CSS 规范

**响应式设计**:
- 移动端优先（mobile-first）
- 断点顺序：默认 → sm: → md: → lg: → xl: → 2xl:
- 示例：`text-sm sm:text-base md:text-lg lg:text-xl`

**深色模式**:
- 所有颜色类必须有 dark: 变体
- 示例：`bg-white dark:bg-gray-800 text-gray-900 dark:text-gray-100`
- 边框和阴影也要适配：`border-gray-200 dark:border-gray-700`

**样式组织**:
- 避免内联 style，优先使用 Tailwind 类
- 复杂样式使用 `<style>` 标签：
  ```blade
  @push('styles')
  <style id="unique-id-v1">
      .custom-class {
          /* 自定义样式 */
      }
  </style>
  @endpush
  ```

**常用模式**:
- 按钮：`rounded-md px-3 py-2 text-sm font-medium transition-all duration-300`
- 卡片：`rounded-lg shadow-md bg-white dark:bg-gray-800 p-4`
- 输入框：`rounded-md border px-3 py-2 focus:ring-2 focus:ring-indigo-500`

### ⚡ Alpine.js 规范

**基本语法**:
- 初始化状态：`x-data="{ open: false, count: 0 }"`
- 条件渲染：`x-show="open"`（保留 DOM）、`x-if="count > 0"`（移除 DOM）
- 事件绑定：`@click="open = !open"`、`@submit.prevent="handleSubmit()"`
- 数据绑定：`x-model="name"`、`x-text="count"`、`x-html="content"`

**过渡效果**:
```html
<div x-show="open"
     x-transition:enter="transition ease-out duration-300"
     x-transition:enter-start="opacity-0 scale-95"
     x-transition:enter-end="opacity-100 scale-100"
     x-transition:leave="transition ease-in duration-200"
     x-transition:leave-start="opacity-100 scale-100"
     x-transition:leave-end="opacity-0 scale-95">
    内容
</div>
```

**最佳实践**:
- 避免复杂逻辑，必要时抽取到 `<script>` 中
- 使用 `x-cloak` 防止闪烁：`<div x-cloak x-show="loaded">`
- 监听全局事件：`window.addEventListener('custom-event', handler)`

### 🌍 国际化规范

**翻译函数**:
- Blade 模板：`{{ __('messages.key') }}`
- 控制器：`__('messages.key')`
- 带参数：`__('messages.welcome', ['name' => $user->name])`

**键名约定**:
- 小写+下划线：`user_menu.profile`、`navigation.home`
- 分层组织：按功能模块分组
- 避免过长的键名

**语言文件位置**:
```
resources/lang/
├── zh_CN/messages.php
├── en/messages.php
├── fr/messages.php
└── ru/messages.php
```

**添加新翻译的流程**:
1. 在 `resources/lang/zh_CN/messages.php` 中添加中文键值
2. 在其他3个语言文件中添加对应翻译
3. 注意法语、俄语文本长度可能更长，测试布局

### 🧪 测试规范

**测试文件位置**:
```
tests/
├── Feature/     # 功能测试
│   └── UserTest.php
└── Unit/        # 单元测试
    └── ImageTest.php
```

**测试命名**:
- 测试方法：`test_` 前缀，描述性命名
- 示例：`test_user_can_upload_image()`

**测试覆盖**:
- 正常流程（happy path）
- 边界条件
- 错误处理

## 🔧 Laravel 特定规则

### 路由和控制器

**RESTful 路由**:
```php
Route::resource('images', ImageController::class);
```

**控制器方法命名**:
- `index()` - 列表页
- `show($id)` - 详情页
- `create()` - 创建表单
- `store(Request $request)` - 存储新记录
- `edit($id)` - 编辑表单
- `update(Request $request, $id)` - 更新记录
- `destroy($id)` - 删除记录

**路由模型绑定**:
```php
Route::get('/users/{user}', [UserController::class, 'show']);
// 自动注入 User 模型实例
public function show(User $user) { }
```

### Eloquent 模型

**基本定义**:
```php
class Image extends Model
{
    protected $fillable = ['title', 'filename', 'path'];

    protected $casts = [
        'is_public' => 'boolean',
        'created_at' => 'datetime',
    ];
}
```

**关联关系**:
```php
// 一对多
public function images() {
    return $this->hasMany(Image::class);
}

// 多对一
public function user() {
    return $this->belongsTo(User::class);
}
```

### 视图缓存管理

**开发环境**:
```bash
# 清除视图缓存
php artisan view:clear

# 清除配置缓存
php artisan config:clear

# 清除路由缓存
php artisan route:clear
```

**生产环境**:
```bash
# 优化缓存（生成缓存文件）
php artisan view:cache
php artisan config:cache
php artisan route:cache

# 或使用一键优化
php artisan optimize
```

**重要提醒**:
- Blade 模板修改后必须执行 `php artisan view:clear`
- 否则修改不会生效（因为使用了缓存的编译结果）
- 可以删除编译文件：`rm -rf storage/framework/views/*.php`

## 📋 文件结构规范

```
<project>/.claude/
    ├── context-summary/              ← 上下文摘要目录
    │   ├── task1.md
    │   └── task2.md
    ├── operations-log.md             ← 操作记录（可选）
    └── verification-report.md        ← 验证报告（可选）
```

## 🎯 标准工作流程

### 完整流程（8步）

1. **分析需求** → 使用 sequential-thinking 深度分析需求，识别关键疑问
2. **评估复杂度** → 确定任务复杂度（简单/中等/复杂）
3. **检索上下文** → 执行7步强制检索清单
4. **验证充分性** → 7项检查必须全部通过
5. **生成摘要** → `.claude/context-summary-[任务名].md`
6. **开始编码** → 遵循项目约定，使用可复用组件
7. **清除缓存** → `php artisan view:clear && php artisan view:cache`
8. **验证功能** → 测试所有语言（中英法俄）和主题模式（亮色/深色）

### 快速流程（简单任务）

1. **分析需求** → 快速评估
2. **检索上下文** → 执行步骤1-3
3. **开始编码** → 遵循项目约定
4. **清除缓存** → `php artisan view:clear`
5. **验证功能** → 快速测试

## ⚠️ 重要提醒

### 绝对禁止

- ❌ 跳过上下文检索直接编码
- ❌ 重复创建已存在的组件
- ❌ 忽略国际化要求（必须支持4种语言）
- ❌ 忘记清除 Blade 视图缓存
- ❌ 只测试一种语言或主题模式
- ❌ 使用内联 style 而非 Tailwind 类（除非必要）
- ❌ 硬编码文本而非使用 `__('messages.key')`

### 必须做到

- ✅ 编码前至少阅读3个相似实现
- ✅ 复用现有 Blade 组件
- ✅ 所有文本使用国际化（中英法俄）
- ✅ 支持响应式（sm:/md:/lg:）和深色模式（dark:）
- ✅ 修改后清除并重建缓存
- ✅ 测试所有4种语言和两种主题模式
- ✅ 验证移动端和桌面端布局

## 🚀 任务开始前强制检查

在开始任何开发任务前，必须执行以下检查：

```markdown
□ 已使用 sequential-thinking 梳理问题、识别风险
□ 已评估任务复杂度（简单/中等/复杂）
□ 已确定需要执行的检索步骤（1-3步或完整7步）
□ 已准备好记录上下文摘要文件
□ 已理解 Laravel + Blade + Tailwind + Alpine.js 技术栈约定
```

## 💡 开发哲学

- **渐进式迭代**: 保持每次改动可编译、可验证
- **研读先于编码**: 在实现前研读既有代码或文档，吸收现有经验
- **务实态度**: 优先满足真实需求而非理想化设计
- **表达清晰**: 选择表达清晰的实现，拒绝炫技式写法
- **简单优先**: 偏向简单方案，避免过度架构或早期优化
- **风格一致**: 遵循既有代码风格，包括导入顺序、命名与格式化

## 🎓 持续改进

本文件应随项目发展持续更新：
- 发现新的项目约定时，更新到对应章节
- 识别新的可复用组件时，补充到模板中
- 遇到新的常见问题时，添加到提醒部分
- 优化工作流程后，更新流程说明

---

**版本**: v1.0
**最后更新**: 2025-10-28
**维护者**: Claude Code
