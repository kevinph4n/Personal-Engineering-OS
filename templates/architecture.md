# Architecture for the project 

## Who are the actors here?
- **for example::** Citizen (Input) -> System Output -> Authority receives the information
---

## What do they actors do?
**for example:***
- Citizen: Upload images and Submit additional information, Delete request
- Authority: Approve the request/Review reports, Assign field teams , Monitor dashboard statistics, Mark status (Processing/Resolved)
- System: Process uploads, Run AI analysis, Store reports, Expose API, Notify authority dashboard

---

## Data flow
- ví dụ: Citizen -> React Frontend -> FastAPI Backend -> YOLO -> Detection JSON -> Database -> FastAPI API response -> React dashboard -> Authority

---

## What if...Failed? (Risk management/Fallback strategy) examples:
- YOLO: The project must still work. Because basically this is not a Detection project using AI. AI is just an extension. So instead of making the whole Backend die just because YOLO isn't working, there must be a way for the Authority to manually review the request (Graceful degradation)
- Cloudinary: Instead of Citizen uploads -> Error. Do Citizen uploads -> Image cannot be stored -> Error. Which means the server itself doesn't crash, and the Frontend works perfectly, just the Cloud problem
> **External service failure must not crash the application process**
- Database: Yep this is an important part. But at least if it failed, do not let the whole Backend system down. Basically just make it "Cannot connect/Connect error" -> HTTP 503 -> Frontend: Service unavailable
> If database is completely unavailable -> **Core functionality unavailable, but service itself is still alive** (Partial service outage
- Leaflet (Map): Basically the project must work without a map, give them actors a list view would be great
> **Maps are visualization, not business logic**
> Basically. Don't let them work for each other. Make them work seperately. Like Backend to YOLO OR Backend to Cloudinary. Not YOLO -> Cloudinary and vice versa (Loose Coupling, low coupling and high cohesion)
> e.g:
> Backend
> ├── YOLO
> ├── Cloudinary
> └── Database
> NOT: YOLO -> Cloudinary -> Database
