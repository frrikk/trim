# TRIM

# SPEC-001: Training Diary App

## Background

The Training Diary App is designed to provide users with a platform to record and track their training sessions, including exercises, reps, sets, and additional notes. This digital solution aims to replace traditional paper-based training logs, offering a more efficient and accessible way to monitor fitness progress.

## Requirements

**Must Have:**
- Secure user authentication
- Ability to record training sessions with dates and durations
- Functionality to add exercises to each session with details like reps, sets, and weights
- A user-friendly UI to view and manage past sessions

**Should Have:**
- Real-time updates for shared training sessions
- Data visualization for progress tracking

**Could Have:**
- Social features to share sessions with friends or coaches
- Integration with fitness trackers and wearables

**Won't Have (for MVP):**
- Advanced analytics and machine learning recommendations
- E-commerce integrations for purchasing fitness equipment

## Method

### Backend Service
Using Supabase for the backend, including PostgreSQL for the database, authentication, and real-time capabilities.

#### Database Schema

- **Users Table**: To store user accounts and profiles.
  - `user_id` (Primary Key, UUID)
  - `email` (String, Unique)
  - `password` (Encrypted String)
  - `name` (String)
  - `created_at` (Timestamp)

- **Sessions Table**: To record each training session, linked to a user.
  - `session_id` (Primary Key, UUID)
  - `user_id` (Foreign Key, UUID, references Users)
  - `date` (Date)
  - `duration` (Integer, in minutes)
  - `notes` (Text, nullable)

- **Exercises Table**: To store exercises that could be part of a session.
  - `exercise_id` (Primary Key, UUID)
  - `session_id` (Foreign Key, UUID, references Sessions)
  - `name` (String)
  - `reps` (Integer)
  - `sets` (Integer)
  - `weight` (Integer, nullable, in lbs or kg)

### Frontend Application
Developed with Next.js 14, leveraging the app directory for enhanced routing and organization.

- **App Structure:**
  - Pages and routing using `page.tsx` files
  - Shared layouts with `layout.tsx`
  - Reusable UI components in `ui/`
  - Custom hooks in `hooks/`
  - API client setup in `lib/`
  - Global styles in `styles/`

## Implementation

1. Set up the Supabase project and initialize the database schema.
2. Implement authentication using Supabase Auth.
3. Develop the backend API for CRUD operations on training sessions and exercises.
4. Scaffold the Next.js application, setting up the app directory structure.
5. Create UI components for the application's main features.
6. Integrate the frontend with the Supabase backend.

## Milestones

1. **Backend Setup**: Completion of the database schema and basic CRUD operations.
2. **Authentication Flow**: Secure login and signup functionality.
3. **Core Frontend**: Key pages and components for session recording and viewing.
4. **Feature Completion**: All "Must Have" features implemented and tested.
5. **Beta Release**: Initial release for user testing and feedback.
6. **Final Release**: Incorporation of feedback and launch of the MVP.

## Gathering Results

Post-MVP, we will collect user feedback to evaluate the app's usability and functionality. Key metrics will include user engagement, session data accuracy, and feedback on the UI/UX. This evaluation will guide further development and feature enhancements.
