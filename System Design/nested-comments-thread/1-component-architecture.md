# Component Architecture: Recursive Nesting

To build a Reddit-style thread, we need a component that can render itself to handle infinite levels of replies.

### 1. `<ThreadContainer />`

- **Role:** The entry point. Fetches the initial "Top Level" comments.
- **Responsibility:** Handles sorting logic (New, Top, Old).

### 2. `<CommentNode />` (The Recursive Engine)

- **Role:** Displays the comment content (Author, Body, Votes).
- **Recursion:** Inside its render block, it checks if `replies` exist. If yes, it maps over them and renders more `<CommentNode />` components.
- **State:** Local state for `isCollapsed` to hide/show children.

### 3. `<Editor />` (Polymorphic)

- **Role:** Used for both "New Reply" and "Edit Comment."
- **Logic:** Controlled component that triggers the "Update" or "Create" action in our state manager.
