# Alpine.js Best Practices

## State Management

### Local State

- 使用 `x-data` 管理元件內部狀態，避免在 `<body>` 上放置大型 `x-data` 物件。

### Global State

- 使用 `Alpine.store()` 管理跨元件共享狀態（如 authentication、theme settings）。

### Store Organization

- 按領域組織 stores（如 `$store.auth`、`$store.cart`），將相關資料和方法分組。

## Reactivity

### Computed Properties

- 在 stores 中使用 getter methods 實作計算屬性（如購物車總額）。

### Reactive Updates

- 理解 Alpine 的 Proxy-based reactivity 系統，避免不必要的重新渲染。

### Lifecycle Hooks

- 適當使用 `x-init`、`x-effect`、`$watch` 和 `$dispatch` 管理元件生命週期。

## Component Patterns

### Scoped Components

- 每個元件使用獨立的 `x-data` scope，避免狀態污染。

### Event Handling

- 使用 `@click`、`@submit` 等事件處理器，配合 `$dispatch` 進行跨元件通訊。

### Conditional Rendering

- 使用 `x-show` 和 `x-if` 進行條件渲染，注意效能差異：
  - `x-show`：使用 CSS display 控制顯示
  - `x-if`：完全移除 DOM 元素

### List Rendering

- 使用 `x-for` 進行列表渲染，記得提供 `:key` 屬性。

### Initialization

- 使用 `x-cloak` 防止未初始化內容閃現。

## Common Patterns

### 建立互動元件

```html
<!-- user-profile.html -->
<div x-data="{ name: 'John Doe', email: 'john@example.com' }"
     class="flex flex-col space-y-2 p-4 bg-white rounded-lg shadow-md">
  <h2 class="text-xl font-semibold text-gray-800" x-text="name"></h2>
  <p class="text-gray-600" x-text="email"></p>
</div>
```

### 使用 x-data 管理狀態和 API 呼叫

```html
<div x-data="{
  data: null,
  loading: true,
  error: null,
  async init() {
    try {
      this.loading = true;
      const response = await fetch('/api/data');
      const result = await response.json();
      this.data = result;
    } catch (err) {
      this.error = err.message;
    } finally {
      this.loading = false;
    }
  }
}" x-cloak>
  <div x-show="loading" class="text-center p-4">Loading...</div>
  <div x-show="error" class="text-red-500 p-4" x-text="'Error: ' + error"></div>
  <div x-show="data" class="p-4">
    <!-- Render data -->
  </div>
</div>
```

### 條件渲染和列表

```html
<div x-data="{ items: ['Item 1', 'Item 2', 'Item 3'], showList: true }">
  <button @click="showList = !showList"
          class="mb-4 px-4 py-2 bg-blue-500 text-white rounded">
    Toggle List
  </button>

  <ul x-show="showList"
      x-transition
      class="space-y-2">
    <template x-for="item in items" :key="item">
      <li class="p-2 bg-gray-100 rounded" x-text="item"></li>
    </template>
  </ul>
</div>
```
