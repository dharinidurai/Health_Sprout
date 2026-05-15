# HealthSprout - AI-Powered Nutrition Monitoring App

Complete mobile-first web app for science-driven nutrition monitoring in South India with multi-role support (User, Doctor, Admin).

## Features

### User Features
- **Splash & Onboarding**: Beautiful intro screen with age group selection, profile creation, and meal schedule consent
- **Dashboard**: BMI tracking, daily meal plans, points/gamification widget, reminders
- **Meal Management**: Log meals, upload photos, track nutrition (calories, protein, micronutrients)
- **Symptom Checker**: AI-powered symptom analysis with deficiency probability detection
- **Doctor Consultation**: Discover nearby verified doctors, view ratings/languages, book time slots, pay online
- **Profile**: Personal health data, language selection, privacy settings, reduced-motion accessibility

### Doctor Features
- **Dashboard**: Appointment queue, patient case view with health analytics
- **Patient Analysis**: BMI history, meal photos, symptom inference, AI-detected deficiencies
- **Meal Plan Management**: Approve/modify AI-generated meal plans, prescribe supplements
- **Availability**: Set consultation hours, manage calendar
- **Patient Chat**: Secure messaging pre/post consultation

### Admin Features
- **Analytics Dashboard**: User growth, consultation metrics, platform health
- **User Management**: Bulk operations, verification status, suspension/reactivation
- **Doctor Verification**: Approve/deny provider credentials
- **Content Moderation**: Review flagged meals, manage inappropriate content
- **Clinical Thresholds**: Configure BMI limits, calorie targets, nutrient recommendations
- **Audit Logs**: Track admin/doctor PII access

## Tech Stack

- **Frontend**: Next.js 16 (App Router), React, TypeScript, Tailwind CSS v4
- **UI Components**: shadcn/ui with custom mint-green theme
- **Charts**: Recharts for BMI trends and analytics
- **State**: Client-side with localStorage (demo)
- **Deployment**: Vercel

## Design System

**Color Scheme**:
- Primary: Mint Green (oklch(0.55 0.15 160))
- Secondary: Soft White/Gray
- Accent: Darker Mint
- High contrast text for accessibility

**Typography**:
- Headings: Geist (bold)
- Body: Geist (regular)
- Mono: Geist Mono

**Animations**:
- Smooth transitions (< 300ms)
- Reduced-motion support via toggle
- Subtle parallax on scroll
- Springy FAB interactions

## Routes

### User Routes
- `/` - Splash screen
- `/login` - Login page
- `/signup` - Sign up with OTP
- `/role-select` - Role selection
- `/onboarding/age` - Age group selection
- `/onboarding/profile` - Profile creation
- `/onboarding/consent` - Meal schedule consent
- `/home` - Dashboard
- `/meals` - Meal tracking
- `/add` - Add meal/symptom modal
- `/symptoms` - Symptom checker
- `/symptoms/results` - AI analysis results
- `/consult` - Doctor discovery & bookings
- `/consult/[doctorId]` - Doctor profile & booking
- `/payment` - Payment gateway
- `/bmi-history` - BMI trends & RNN forecast
- `/profile` - Profile & settings

### Doctor Routes
- `/doctor/onboarding` - Verification setup
- `/doctor/dashboard` - Appointment queue & patient cases

### Admin Routes
- `/admin/onboarding` - Admin setup
- `/admin/dashboard` - Platform management

## Demo Credentials

\`\`\`
Email: demo@healthsprout.com
Password: demo123
\`\`\`

## Key Components

- `MobileNavigation` - Bottom tab bar with central FAB
- `ProfileCard` - User profile header with bio
- `BMICard` - BMI status display
- `MealPlanCard` - Individual meal logging
- `PointsWidget` - Gamification points tracker
- All components use smooth animations and mobile-first design

## Data Models (Conceptual)

\`\`\`json
User: {
  id, name, dob, age, sex, height_cm, weight_kg,
  dietary_type, location {state, city, pincode},
  activities[], disabilities[], points, role
}

BMIEntry: { user_id, timestamp, weight, height, bmi }

MealPlan: {
  user_id, date, meals[{type, recipe_id, nutrients}]
}

Doctor: {
  id, name, specialization, verified, location {lat, lng},
  availability[], languages[], rating, reviews
}

Appointment: {
  id, user_id, doctor_id, slot_start, slot_end,
  status {requested, approved, declined, completed}
}
\`\`\`

## API Endpoints (Stubs)

Future integration points:
- `POST /infer/symptoms` - AI symptom analysis
- `POST /bmi` - BMI calculation & percentile
- `POST /plan/generate` - LP-optimized meal planning
- `GET /doctors/nearby` - Geo-based doctor discovery
- `POST /upload/meal-photo` - Image upload to S3

## Getting Started

\`\`\`bash
# Install dependencies
npm install

# Run development server
npm run dev

# Open http://localhost:3000
\`\`\`

## Accessibility

- ✓ High contrast text (WCAG AA)
- ✓ Semantic HTML
- ✓ ARIA labels
- ✓ Reduced-motion toggle
- ✓ Keyboard navigation
- ✓ Screen reader support

## Next Steps (For Production)

1. **Backend**: Node.js/Python + PostgreSQL/Supabase for user, doctor, appointment data
2. **ML Models**: Implement RNN for BMI forecasting, VAE for symptom encoding, LP solver for meal optimization
3. **Authentication**: Supabase Auth with OTP via Twilio
4. **Storage**: Vercel Blob or AWS S3 for meal photos
5. **Payments**: Stripe integration for consultation fees
6. **Localization**: i18n setup for Tamil, Telugu, Kannada, Malayalam
7. **Maps**: Google Maps API for doctor location discovery
8. **Video**: Agora/Twilio for in-app video consultations
9. **Push Notifications**: Firebase Cloud Messaging for appointment reminders
10. **Testing**: Jest + React Testing Library + Playwright E2E

## Deployment

Ready for deployment to Vercel:
\`\`\`bash
vercel deploy
\`\`\`

## License

Proprietary - HealthSprout Inc.
