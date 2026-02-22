# 📊 System Design: Generic Filterable Dashboard

**The Challenge:** Design a scalable dashboard that can filter through high-frequency data (like Orders or Customers).

- **Left Pane:** Dynamic filters (Text, Dates, Dropdowns).
- **Right Pane:** Results showing 20 items at a time.
- **The Catch:** Data is growing fast (10 new orders/second). We must support infinite scrolling with **zero gaps** and **zero duplicates**.

**Learning Objective:** How to design extensible "config-driven" UI components and handle real-time data pagination without messing up the user experience.
