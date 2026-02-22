# API Design Contract

To make this generic, the API should accept a dynamic filter payload and a cursor.

**Endpoint:** `POST /api/v1/search/:entity`
_(Note: We use POST instead of GET because a complex filter object can get too large for a standard URL query string)._

### Request Payload

```typescript
interface SearchRequest {
  entity: "orders" | "customers"; // Passed in URL or body
  limit: 20; // Fixed size
  cursor: string | null; // ISO Timestamp or unique ID of the last item
  filters: {
    orderId?: string;
    status?: string[]; // Allow multiple selections
    createdBetween?: { start: string; end: string };
  };
}
```
