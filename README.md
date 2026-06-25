# Preorder Management

A responsive preorder management dashboard built with Next.js, TypeScript, Tailwind CSS, and Axios. It connects to a backend API for listing, filtering, sorting, paginating, creating, updating, status toggling, and deleting preorder records.

Live site: https://preorder-management-01.vercel.app

## Features

- Preorder list with backend-driven filtering, sorting, and pagination
- Status filters for All, Active, and Inactive preorders
- Sort controls for name, created date, start date, and end date
- Row selection and select-all checkbox support
- Create preorder form with validation
- Update preorder form with pre-filled values
- Active/inactive status update directly from the table
- Delete confirmation modal before removing a preorder
- Shadcn-style calendar popover for date and time selection
- Toast feedback for create, update, delete, and status changes
- Fully responsive layout with horizontal table scrolling on small screens
- Custom not-found page

## Tech Stack

- Next.js 16
- React 19
- TypeScript
- Tailwind CSS 4
- Axios
- Sonner
- Framer Motion
- Radix UI Popover
- React DayPicker
- date-fns

## Getting Started

Install dependencies:

```bash
yarn install
```

Create a `.env.local` file in the project root:

```env
NEXT_PUBLIC_BASE_URL="https://preorder-management-backend.onrender.com"
```

Start the development server:

```bash
yarn dev
```

Open http://localhost:3000 in your browser.

## Available Scripts

```bash
yarn dev
```

Runs the app in development mode.

```bash
yarn build
```

Creates a production build.

```bash
yarn start
```

Runs the production build locally.

```bash
yarn lint
```

Runs ESLint.

## API Integration

The app uses `NEXT_PUBLIC_BASE_URL` as the API base URL. API requests are handled through `lib/api-client.ts` and `lib/preorders.ts`.

Expected endpoints:

```http
GET /preorder
POST /preorder
PATCH /preorder/{id}
DELETE /preorder/{id}
```

List query parameters:

```http
/preorder?search=summer&status=active&sortBy=createdAt&sortOrder=desc&page=1&limit=10
```

Supported values:

- `status`: `all`, `active`, `inactive`
- `sortBy`: `name`, `createdAt`, `startsAt`, `endsAt`
- `sortOrder`: `asc`, `desc`
- `page`: number
- `limit`: number

## Project Structure

```text
app/
  layout.tsx
  page.tsx
  not-found.tsx
components/
  preorders/
    preorder-management-page.tsx
    preorder-table.tsx
    preorder-filters.tsx
    preorder-pagination.tsx
    preorder-form.tsx
    confirm-delete-modal.tsx
    date-time-picker.tsx
  ui/
    calendar.tsx
    popover.tsx
lib/
  api-client.ts
  preorder-options.ts
  preorders.ts
types/
  preorder.ts
```

## Notes

- Filtering, sorting, and pagination are expected to be handled by the backend.
- The frontend updates the current list after mutations without a full page refresh.
- `.env.local` is ignored by Git, so each environment needs its own API base URL.
