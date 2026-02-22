# State Management & Data Flow

### The Pagination Problem: Why Offset Pagination Fails Here

The interviewer: _10 new orders are created per second._
If we use traditional **Offset Pagination** (`page=1`, `limit=20`), we will get duplicates.

- _Why?_ Imagine you are on Page 1 (items 1-20). In the 5 seconds it takes you to scroll, 50 new orders arrive at the top of the database. When you request Page 2 (items 21-40), the original items from Page 1 have been pushed down into Page 2's slot. The user will see duplicate orders!

### The Solution: Cursor-Based Pagination

Instead of saying "Give me page 2," we say, "Give me 20 items that were created _older than_ this specific timestamp (the cursor)."

- Even if 1,000 new orders arrive, they won't affect our query for older items. This guarantees **no gaps and no duplicates**.

### State Management Choices

To handle this cleanly, we split our state into two categories:

1. [cite_start]**Client State (Jotai / React Context)** [cite: 71]
   - We need a localized state for the `FilterPanel`. If a user is typing an Order ID but hasn't clicked "Submit", the right pane _should not_ update yet.
   - [cite_start]**Why Jotai?** It's atomic and lightweight, perfect for isolating this "Draft Form State" without causing re-renders in the Results Panel[cite: 71].

2. [cite_start]**Server State (React Query / SWR)** [cite: 71]
   - We need a robust tool to handle the API data.
   - **Why React Query?** It has a built-in `useInfiniteQuery` hook. It automatically handles the cursor math, deduplicates API requests, caches the pages, and gives us out-of-the-box `isFetchingNextPage` booleans.
