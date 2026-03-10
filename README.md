# LuxeStay — Hotel Booking & Room Management System

> **Angular 17 · TypeScript · Angular Material · RxJS**  
> Project 20 — Full-stack SPA with hotel listings, booking, admin management

---

## 🚀 Quick Start (2 Steps)

```bash
# 1. Install dependencies
npm install

# 2. Run the app
ng serve
# → Open http://localhost:4200
```

> No backend needed — data loads from `src/assets/db.json` automatically.
> Optional: `npm run mock-api` for a live REST API on port 3000.

---

## 🔐 Demo Credentials

| Role  | Email                  | Password  |
|-------|------------------------|-----------|
| Guest | any valid email        | 6+ chars  |
| Admin | admin@luxestay.com     | admin123  |

---

## 📁 Project Structure

```
hotelapp/
├── src/
│   ├── app/
│   │   ├── components/
│   │   │   ├── navbar/           # Navigation + Auth modal (template-driven forms)
│   │   │   ├── hotel-list/       # Home hero + hotel grid with filters
│   │   │   ├── hotel-detail/     # Hotel info + rooms with MatExpansionPanel + tabs
│   │   │   ├── booking-form/     # Full Reactive Form with cross-field validators
│   │   │   ├── user-dashboard/   # Guest bookings & stats (combineLatest + AuthGuard)
│   │   │   └── admin-panel/      # MatTable + room management (AdminGuard)
│   │   ├── services/
│   │   │   ├── hotel.service.ts  # HttpClient + BehaviorSubject + search/filter
│   │   │   ├── booking.service.ts# Booking CRUD + localStorage persistence
│   │   │   └── user.service.ts   # Auth state management (BehaviorSubject)
│   │   ├── models/
│   │   │   ├── hotel.model.ts    # Hotel/Room interfaces + HotelModel/RoomModel classes
│   │   │   ├── booking.model.ts  # Booking interface + BookingModel class
│   │   │   └── user.model.ts     # User interface + UserModel class + DTOs
│   │   ├── guards/
│   │   │   └── guards.ts         # AuthGuard + AdminGuard (CanActivate)
│   │   ├── interceptors/
│   │   │   └── loading.interceptor.ts  # HTTP_INTERCEPTORS + LoadingService
│   │   ├── pipes/
│   │   │   └── custom.pipes.ts   # rupee, ratingStars, hotelFilter, nights, timeSince
│   │   ├── directives/
│   │   │   └── custom.directives.ts  # FullyBookedDirective, DiscountBadgeDirective
│   │   ├── app-routing.module.ts
│   │   ├── app.module.ts
│   │   └── app.component.ts
│   ├── assets/
│   │   └── db.json              # Static mock data (6 hotels, 18 rooms)
│   ├── environments/
│   │   ├── environment.ts
│   │   └── environment.prod.ts
│   ├── styles.scss              # Global styles + CSS variables (luxury gold theme)
│   └── index.html
├── angular.json                 # With dev + production configurations
├── package.json
└── tsconfig.json
```

---

## 🛣️ Routes

| Path                    | Component             | Guard      |
|-------------------------|-----------------------|------------|
| `/`                     | → redirect `/home`    |            |
| `/home`                 | HotelListComponent    |            |
| `/hotels`               | HotelListComponent    |            |
| `/hotel/:id`            | HotelDetailComponent  |            |
| `/hotel/:id/:type`      | HotelDetailComponent  |            |
| `/book/:hotelId/:roomId`| BookingFormComponent  | AuthGuard  |
| `/dashboard`            | UserDashboardComponent| AuthGuard  |
| `/admin`                | AdminPanelComponent   | AdminGuard |

---

## ✅ Angular Features Covered

### Components & Templates
- `*ngIf`, `*ngFor`, `*ngTemplateOutlet` structural directives
- `[ngClass]`, `[ngStyle]` attribute binding
- `(click)`, `(input)`, `(ngSubmit)` event binding
- Interpolation, property binding, two-way `[(ngModel)]`

### Routing
- `RouterModule.forRoot()` with `scrollPositionRestoration`
- Dynamic route params (`:id`, `:hotelId/:roomId`)
- Child routes for room categories
- `routerLink`, `routerLinkActive`
- Route guards: `AuthGuard` + `AdminGuard` (`CanActivate`)

### Forms
- **Reactive Forms** — booking & admin forms (`FormBuilder`, `Validators`, cross-field validator)
- **Template-driven Forms** — navbar auth, login/register (`ngModel`, `NgForm`)
- Custom validator: `dateRangeValidator` (check-out > check-in)
- Inline validation messages with `hasError()` / `ng-touched`

### Services & DI
- `HotelService` — `HttpClient`, caching, search/filter
- `BookingService` — CRUD, localStorage persistence, stats
- `UserService` — auth state, BehaviorSubject, role detection
- `LoadingService` — shared loading state

### RxJS
- `BehaviorSubject`, `combineLatest`, `switchMap`, `takeUntil`
- `debounceTime`, `distinctUntilChanged`, `map`, `tap`, `catchError`

### Custom Pipes
- `rupee` — formats numbers as ₹12,500
- `ratingStars` — converts 4 → ★★★★☆
- `hotelFilter` — full-text search across hotels
- `nights` — "3 nights" label
- `timeSince` — "2h ago" relative time

### Custom Directives
- `[appFullyBooked]` — dims unavailable rooms visually
- `[appDiscount]` — injects a discount badge ribbon

### Angular Material
- `MatProgressBar` — global loading indicator
- `MatSnackBar` — booking success/error toasts
- `MatTable` — admin bookings data table
- `MatExpansionPanel` — hotel amenities
- `MatTooltip` — action button labels
- `MatSpinner` — async loading states
- `MatDivider` — visual separators

### HTTP & Error Handling
- `HTTP_INTERCEPTORS` — `LoadingInterceptor` with `finalize`
- Graceful fallback from JSON Server → static assets

---

## 🏨 Mock Data (src/assets/db.json)
- **6 Hotels**: Mumbai, Bengaluru, Udaipur, Alleppey, Manali, Goa
- **18 Rooms**: Standard, Deluxe, Suite per hotel
- Bookings and users are stored in `localStorage`

---

## 🎨 Design
- **Theme**: Luxury warm gold (`#d4af78`) on deep charcoal (`#0f0e0c`)
- **Fonts**: Cormorant Garamond (display) + Outfit (body) + Space Mono (numbers)
- **Fully responsive** — mobile-first grid layouts
