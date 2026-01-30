# Tailwind CSS Best Practices

## Utility-First Approach

### 直接使用 Utilities

- 優先使用 Tailwind 的 utility classes，避免自訂 CSS。

### Responsive Design

- 使用 responsive prefixes 實作響應式設計：
  - `sm:` - 640px 以上
  - `md:` - 768px 以上
  - `lg:` - 1024px 以上
  - `xl:` - 1280px 以上
  - `2xl:` - 1536px 以上

### Dark Mode

- 使用 `dark:` prefix 實作深色模式支援。

## Component Patterns

### Reusable Classes

- 對於重複使用的樣式組合，考慮使用 `@apply` 或建立 component classes。

### Spacing Consistency

- 使用 Tailwind 的 spacing scale 保持一致的間距。

### Color Palette

- 使用 Tailwind 的預設 color palette 或自訂 theme colors。

## Performance

### PurgeCSS

- 確保 Tailwind 正確配置 PurgeCSS 以移除未使用的 styles。

### JIT Mode

- 使用 Tailwind JIT mode 以獲得更好的開發體驗和效能。

## Common Patterns

### 響應式 Grid 佈局

```html
<div class="
  grid
  grid-cols-1
  md:grid-cols-2
  lg:grid-cols-3
  gap-4
  p-4
">
  <!-- Grid items -->
</div>
```

### Flexbox 置中

```html
<div class="flex items-center justify-center min-h-screen">
  <!-- Centered content -->
</div>
```

### Card 元件

```html
<div class="bg-white rounded-lg shadow-md p-6 hover:shadow-lg transition-shadow">
  <h3 class="text-lg font-semibold text-gray-800">Card Title</h3>
  <p class="text-gray-600 mt-2">Card content goes here.</p>
</div>
```

### Button 樣式

```html
<!-- Primary Button -->
<button class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 focus:ring-2 focus:ring-blue-300 transition-colors">
  Primary
</button>

<!-- Secondary Button -->
<button class="px-4 py-2 bg-gray-200 text-gray-800 rounded hover:bg-gray-300 focus:ring-2 focus:ring-gray-300 transition-colors">
  Secondary
</button>
```

### Form Input

```html
<input
  type="text"
  class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
  placeholder="Enter text..."
>
```
