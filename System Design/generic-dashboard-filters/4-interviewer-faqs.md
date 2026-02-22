# 🧠 Interviewer FAQs & Edge Cases

Here are common follow-up questions an interviewer might ask after you present this design:

**Q1: What happens if the user scrolls down 50 pages? Won't rendering 1,000 DOM nodes slow down the browser?**

- **Answer:** Yes, a massive DOM will cause scroll lag and memory leaks. To fix this, I would implement **DOM Virtualization** (using a library like `react-window` or `react-virtualized`). This technique only renders the items currently visible in the viewport plus a small buffer, keeping the DOM size strictly capped at around 30-40 nodes regardless of how much we've fetched.

**Q2: What if the API call fails while fetching the next 20 items?**

- **Answer:** React Query handles this beautifully. It will change its `isError` state. We would render an inline "Failed to load more. Tap to retry" button at the bottom of the list, rather than crashing the whole dashboard.

**Q3: If the user changes a filter and clicks submit, what happens to the infinite scroll?**

- **Answer:** The "Active Search State" changes. This acts as a dependency array trigger. We must clear the React Query cache for the previous search, reset the `cursor` to `null`, and scroll the user back to the top of the `ResultsPanel` before fetching the new batch of 20 results.
