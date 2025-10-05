# TASKS.md

## Project Overview
TrailRunPlanner is a comprehensive web application designed to help trail runners create personalized training and nutrition plans for their races. The platform will support everything from 10K trail races to ultra-marathons, providing custom schedules, nutrition optimization, and race simulation features.

## Core Requirements

### 1. User Management
- [ ] User registration and authentication system
- [ ] User profiles with personal data (age, weight, experience level, goals)
- [ ] Dashboard for personal overview

### 2. Training Plan Management
- [ ] Create custom training plans based on race distance and date
- [ ] Pre-built training templates for different race types (10K, half-marathon, marathon, ultra)
- [ ] Weekly/monthly training schedule views
- [ ] Integration with popular running apps (Strava, Garmin Connect)
- [ ] Training log and progress tracking
- [ ] Workout library (intervals, tempo runs, long runs, recovery)

### 3. Nutrition Planning
- [ ] Personalized nutrition plans based on training phase
- [ ] Race-day nutrition strategies
- [ ] Calorie and macro tracking
- [ ] Food database and meal suggestions
- [ ] Hydration planning and reminders

### 4. Race Preparation
- [ ] Race simulation tools
- [ ] Terrain-specific training recommendations
- [ ] Elevation profile analysis
- [ ] Weather condition planning
- [ ] Gear recommendations and checklists

### 5. Analytics and Progress Tracking
- [ ] Performance analytics dashboard
- [ ] Progress visualization (charts, graphs)
- [ ] Goal tracking and achievement system
- [ ] Training load monitoring

### 6. Community Features
- [ ] Share training plans with community
- [ ] Rate and review training templates
- [ ] Discussion forums
- [ ] Group challenges and events

## Technical Architecture

### Frontend (React/Next.js)
```
frontend/
├── src/
│   ├── components/
│   │   ├── auth/
│   │   ├── dashboard/
│   │   ├── training/
│   │   ├── nutrition/
│   │   ├── analytics/
│   │   └── common/
│   ├── pages/
│   │   ├── auth/
│   │   ├── dashboard/
│   │   ├── training/
│   │   ├── nutrition/
│   │   ├── race-prep/
│   │   └── community/
│   ├── hooks/
│   ├── services/
│   ├── utils/
│   └── types/
├── public/
├── styles/
└── package.json
```

### Backend (Python/FastAPI)
```
backend/
├── app/
│   ├── api/
│   │   ├── auth/
│   │   ├── users/
│   │   ├── training/
│   │   ├── nutrition/
│   │   ├── analytics/
│   │   └── community/
│   ├── core/
│   │   ├── config.py
│   │   ├── security.py
│   │   └── database.py
│   ├── models/
│   │   ├── user.py
│   │   ├── training.py
│   │   ├── nutrition.py
│   │   └── race.py
│   ├── services/
│   │   ├── training_service.py
│   │   ├── nutrition_service.py
│   │   ├── analytics_service.py
│   │   └── external_integrations.py
│   └── utils/
├── migrations/
├── tests/
└── requirements.txt
```

### Database Schema (PostgreSQL)
- **Users**: id, email, password_hash, profile_data, created_at
- **Training_Plans**: id, user_id, name, race_type, start_date, end_date, template_id
- **Workouts**: id, plan_id, date, type, duration, distance, intensity, notes
- **Nutrition_Plans**: id, user_id, daily_calories, macros, meal_schedule
- **Races**: id, user_id, name, date, distance, elevation_gain, location
- **Progress_Logs**: id, user_id, date, metrics (weight, resting_hr, etc.)

## Development Phases

### Phase 1: Foundation (Weeks 1-4)
- [ ] Set up development environment
- [ ] Create basic project structure
- [ ] Implement user authentication
- [ ] Design database schema
- [ ] Create basic UI components
- [ ] Ensure local deployment setup for both frontend and backend

### Phase 2: Core Training Features (Weeks 5-8)
- [ ] Training plan creation and management
- [ ] Workout library implementation
- [ ] Calendar integration
- [ ] Basic progress tracking
- [ ] Refine local deployment setup for testing

### Phase 3: Nutrition System (Weeks 9-12)
- [ ] Nutrition plan creation
- [ ] Food database integration
- [ ] Meal planning interface
- [ ] Calorie/macro tracking
- [ ] Prepare components for deployment readiness

### Phase 4: Advanced Features (Weeks 13-16)
- [ ] Race simulation tools
- [ ] Analytics dashboard
- [ ] External app integrations
- [ ] Mobile responsiveness
- [ ] Transition to deployable setup (e.g., Vercel for frontend, Railway/Heroku for backend)

### Phase 5: Community & Polish (Weeks 17-20)
- [ ] Community features
- [ ] Performance optimization
- [ ] Testing and bug fixes
- [ ] Finalize deployment setup and documentation

## Tech Stack

### Frontend
- **Framework**: Next.js 14 with TypeScript
- **Styling**: Tailwind CSS
- **State Management**: Zustand or Redux Toolkit
- **Charts**: Chart.js or Recharts
- **Forms**: React Hook Form with Zod validation

### Backend
- **Framework**: FastAPI with Python 3.11+
- **Database**: PostgreSQL
- **ORM**: SQLAlchemy
- **Authentication**: JWT with FastAPI-Users
- **API Documentation**: Automatic with FastAPI/OpenAPI

### DevOps & Tools
- **Containerization**: Docker & Docker Compose
- **Version Control**: Git
- **CI/CD**: GitHub Actions
- **Deployment**: Vercel (frontend) + Railway/Heroku (backend)
- **Monitoring**: Sentry for error tracking

## CI/CD Requirements

### Pre-commit Hooks
- Use `pre-commit` to enforce code quality checks.
- Include `ruff` for linting and code formatting.
- Add `isort` for import sorting.

### Test Coverage
- Ensure a minimum of 90% test coverage for the backend.
- Use `pytest` with `pytest-cov` for test execution and coverage reporting.

### Poetry for Dependency Management
- Use `poetry` to manage Python dependencies.
- Define all dependencies and development tools in `pyproject.toml`.

### GitHub Actions Workflow
- Set up a CI pipeline with the following steps:
  1. Install dependencies using `poetry`.
  2. Run `ruff` for linting and formatting checks.
  3. Execute tests with `pytest` and ensure coverage meets the threshold.
  4. Deploy to the appropriate environment (e.g., Railway/Heroku for backend, Vercel for frontend).

### Example Commands
- Install dependencies: `poetry install`
- Run linting: `ruff backend/`
- Format code: `black backend/`
- Sort imports: `isort backend/`
- Run tests: `pytest --cov=backend/`

## Getting Started

1. Clone the repository
2. Set up Python virtual environment
3. Install backend dependencies: `pip install -r backend/requirements.txt`
4. Install frontend dependencies: `cd frontend && npm install`
5. Set up PostgreSQL database
6. Run migrations
7. Start development servers
