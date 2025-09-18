# Next.js Practice Session (2 Hours)

Welcome to your Next.js practice session! This guide is designed to help you master advanced Next.js concepts through in-depth lessons and challenging practical tasks. This extended session is tailored to be completed in 2 hours of focused effort, showcasing skills that can impress employers with your ability to handle complex scenarios.

## Overview

This practice session covers a wide range of Next.js concepts, from fundamentals to advanced topics, including:
- Project structure, routing, and nested layouts
- Components, props, and state management
- Styling with Tailwind CSS and custom CSS modules
- Data fetching with error handling and caching strategies
- API routes with input validation and authentication basics
- Middleware for request processing and security
- Dynamic routes and server-side rendering optimizations
- Performance optimization with code splitting and lazy loading

## Lessons and Tasks

### Lesson 1: Understanding Next.js Structure, Routing, and Layouts (15 minutes)
**Objective**: Learn the file-system-based routing of Next.js, how to create pages, and use nested layouts for consistent UI.
- **Key Points**:
  - Pages are created in the `app` directory using the App Router, which supports advanced features like React Server Components.
  - File names map to routes (e.g., `page.tsx` in a folder becomes a route).
  - Dynamic routes use square brackets (e.g., `[id]`) for parameterized URLs.
  - Layouts (`layout.tsx`) allow shared UI across pages, supporting nested structures for complex apps.
  - Route groups with parentheses (e.g., `(folder)`) organize routes without affecting the URL structure.
- **Task 1 (10 minutes)**: Create a new page at `client/src/app/practice/about/page.tsx` with a simple "About Us" heading and paragraph. Then, create a `layout.tsx` in `client/src/app/practice/layout.tsx` to wrap all practice pages with a common header (title: "Next.js Practice") and footer (text: "Practice Session 2025"). Visit `/practice/about` in your browser to confirm the layout applies.

### Lesson 2: Building Components with Props and State (20 minutes)
**Objective**: Understand how to create reusable components in Next.js, manage props for data passing, and handle basic state.
- **Key Points**:
  - Components are reusable UI pieces, often placed in a `components` folder outside the `app` directory for better organization.
  - Props allow passing data to components, enabling dynamic content.
  - Use React's `useState` hook for local state management within components (e.g., toggling visibility or counting clicks).
  - Event handlers like `onClick` can update state or trigger actions.
- **Task 2 (15 minutes)**: Create a component at `client/src/components/Card.tsx` that accepts `title` and `description` props. Add a stateful "Like" button to the card that increments a counter when clicked. Use this component in `client/src/app/practice/page.tsx` to display 3 cards with different content and interactive buttons.

### Lesson 3: Styling with Tailwind CSS and CSS Modules (20 minutes)
**Objective**: Apply styles using Tailwind CSS for rapid development and CSS modules for scoped, custom styles.
- **Key Points**:
  - Tailwind CSS uses utility classes for rapid styling (e.g., `bg-blue-500`, `text-center`), scoped globally but customizable via `tailwind.config.js`.
  - CSS modules (files named `*.module.css`) provide scoped styles by generating unique class names, preventing style conflicts.
  - Combine Tailwind for layout and CSS modules for unique component-specific styles.
- **Task 3 (15 minutes)**: Enhance your `Card` component with Tailwind styles (e.g., background color, padding, shadow, border radius). Then, create a CSS module at `client/src/components/Card.module.css` with a custom animation (e.g., hover effect to scale the card slightly). Apply this custom style to your cards and ensure they look visually appealing on the practice page.
- **Challenge (Optional, 5 minutes)**: How to handle style conflicts when multiple CSS sources (global, Tailwind, modules) are used? Research specificity or `!important` usage in Tailwind.

### Lesson 4: Data Fetching with Error Handling and Caching (25 minutes)
**Objective**: Learn advanced data fetching in Next.js, including error handling and caching strategies for performance.
- **Key Points**:
  - With App Router, data fetching can be done server-side (using `async/await` in Server Components) or client-side (using `fetch` with `useEffect` in Client Components).
  - Server Components fetch data at render time on the server, reducing client-side JavaScript.
  - Handle errors with try-catch blocks and display user-friendly messages.
  - Use `revalidate` options or `cache: 'no-store'` in `fetch` to control caching behavior for dynamic data.
- **Task 4 (20 minutes)**: Modify `client/src/app/practice/page.tsx` to fetch a list of 5 items from a free API (like `jsonplaceholder.typicode.com/posts`) as a Server Component. Implement error handling to show a fallback message if the API fails. Display the items using your `Card` component. Add a loading state while fetching. **Challenge**: How to handle rate limiting or network interruptions? Implement a retry mechanism with a maximum of 3 attempts before showing an error.

### Lesson 5: Creating API Routes with Validation and Authentication Basics (25 minutes)
**Objective**: Build a robust API endpoint in Next.js with input validation and a basic understanding of authentication.
- **Key Points**:
  - API routes are defined in `app/api/.../route.ts` with App Router, supporting HTTP methods like `GET`, `POST`, etc.
  - Validate incoming request data (e.g., query params, body) to ensure security and correctness before processing.
  - Authentication can be simulated with headers or tokens (real-world apps use libraries like NextAuth.js).
  - Return appropriate HTTP status codes (e.g., 400 for bad input, 401 for unauthorized).
- **Task 5 (20 minutes)**: Enhance the API route at `client/src/app/api/hello/route.ts` to accept a `POST` request with a JSON body containing a `name` field. Validate that `name` is a non-empty string; if invalid, return a 400 error. If valid, return a personalized greeting. Add a simple authentication check by requiring a header `x-api-key` with a dummy value (e.g., 'secret123'); return a 401 error if missing or incorrect. Test it using a tool like Postman or curl.
- **Challenge (Optional, 5 minutes)**: How to handle CORS issues when your API is called from a different domain? Research enabling CORS in Next.js API routes.

### Lesson 6: Middleware for Request Processing and Security (20 minutes)
**Objective**: Understand how to use Next.js middleware to process requests, enforce security, and customize responses before they reach the application.
- **Key Points**:
  - Middleware runs before each request, allowing URL rewrites, redirects, header modifications, or access control.
  - Defined in `middleware.ts` at the project root, it can filter paths using matcher configurations.
  - Useful for logging, authentication checks, A/B testing, or geo-restrictions.
  - Be cautious of performance impacts since it executes on every request.
- **Task 6 (15 minutes)**: Create a `middleware.ts` file at the root of your project (`client/middleware.ts`) to log incoming request paths to the console for all routes under `/practice/*`. Additionally, redirect requests to `/practice` if the user-agent contains 'mobile' (simulating a mobile-specific landing page). Test this by accessing different `/practice` routes and spoofing the user-agent in browser dev tools.
- **Challenge (Optional, 5 minutes)**: How to handle middleware for API routes without affecting performance? Research skipping middleware for specific paths.

### Lesson 7: Dynamic Routes and Server-Side Rendering Optimizations (20 minutes)
**Objective**: Master dynamic routing with parameterized URLs and optimize server-side rendering for SEO and performance.
- **Key Points**:
  - Dynamic routes use `[param]` syntax to capture URL segments for personalized content (e.g., `/practice/item/[id]`).
  - Server-side rendering (SSR) with `dynamic` export or `getServerSideProps` (in Pages Router) ensures content is fresh on each request, benefiting SEO.
  - Incremental Static Regeneration (ISR) with `revalidate` balances static performance with dynamic updates.
  - Use `dynamicParams` to control which dynamic routes are pre-rendered or rendered on-demand.
- **Task 7 (15 minutes)**: Create a dynamic route at `client/src/app/practice/item/[id]/page.tsx` that displays a mock product page based on the `id` parameter (e.g., "Product ID: 123"). Fetch mock product data from `jsonplaceholder.typicode.com/posts/[id]` and render it server-side. Ensure the page is SEO-friendly by including meta tags with the product title. Test by visiting `/practice/item/1` and inspecting the page source for meta tags.
- **Challenge (Optional, 5 minutes)**: How to handle invalid or non-existent IDs gracefully? Implement a 404 response for bad IDs.

### Lesson 8: Performance Optimization with Code Splitting and Lazy Loading (15 minutes)
**Objective**: Improve application performance by implementing code splitting and lazy loading for faster initial page loads.
- **Key Points**:
  - Code splitting reduces bundle size by loading only necessary JavaScript for the current page.
  - Next.js supports dynamic imports for lazy loading components, reducing initial load time.
  - Use `next/dynamic` to import components only when they are rendered (e.g., below-the-fold content or modals).
  - Combine with suspense boundaries for loading states during lazy loading.
- **Task 8 (10 minutes)**: Create a heavy component at `client/src/components/HeavyComponent.tsx` (simulate heaviness by adding a large array or complex rendering logic). Use `next/dynamic` to lazy load this component in `client/src/app/practice/page.tsx`, showing a loading spinner (use an existing component or create a simple one) while it loads. Inspect the network tab in browser dev tools to confirm the component loads separately.
- **Challenge (Optional, 5 minutes)**: How to handle errors during lazy loading? Research error boundaries with lazy-loaded components.

## Final Notes
- Take short breaks if needed, but aim to complete this in one 2-hour sitting for maximum retention and to simulate a focused work environment.
- If you finish early, tackle the optional challenges or dive deeper into advanced topics like custom server setup, WebSocket integration, or testing with Jest and React Testing Library.
- Refer to the Next.js documentation (https://nextjs.org/docs) for deeper insights on any topic, especially for App Router specifics, middleware, and performance optimizations.
- Reflect on each task: What worked well? What was tricky? How can you apply these advanced skills in a real project to stand out to your employer?

Happy coding with Next.js, and good luck impressing your employer with these advanced skills!
