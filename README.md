# OMDB Movie Explorer - Premium 3D UI

A stunning movie search and discovery platform with premium glassmorphic design, 3D effects, and particle animations. Built with Next.js 16, React 19, and Tailwind CSS v4.

## Features

- **Advanced Search**: Real-time movie and TV series search powered by OMDB API
- **3D Effects**: Glassmorphism, card transforms, particle animations, and gradient effects
- **Movie Details**: Comprehensive information including plot, cast, ratings, and more
- **Favorites Management**: Save and manage your favorite movies
- **Responsive Design**: Fully responsive across all devices
- **Smart Caching**: Dual-tier caching system for optimal performance
- **Setup Guide**: Built-in interactive setup instructions

## System Requirements

Before getting started, ensure you have installed:
- **Node.js**: Version 18.0.0 or higher
- **npm**: Version 9.0.0 or higher (comes with Node.js)
- **Git**: For version control

To check your versions, run:
\`\`\`bash
node --version
npm --version
\`\`\`

## Getting Started - Detailed Setup Steps

### Step 1: Extract and Navigate to Project

1. Download the project ZIP file from v0
2. Extract the ZIP file to your desired location
3. Open your terminal/command prompt
4. Navigate to the project folder:
   \`\`\`bash
   cd path/to/OMDB-Movie-Explorer
   \`\`\`

### Step 2: Install Dependencies

Install all required npm packages:
\`\`\`bash
npm install
\`\`\`

This will download and install all dependencies listed in `package.json`, including:
- Next.js 16
- React 19
- Tailwind CSS v4
- TypeScript
- And other utilities

**Expected output**: You should see "added X packages" when complete. This may take 2-5 minutes depending on your internet speed.

### Step 3: Configure Environment Variables

Create a `.env.local` file in the project root directory with your OMDB API key:

1. Create a new file named `.env.local` in the root directory (same level as `package.json`)
2. Add the following line:
   \`\`\`
   OMDB_API_KEY=d20e1964
   \`\`\`

**Important**: 
- Keep this file private and never commit it to version control
- The file should only contain the API key value, not a full URL
- `.env.local` is automatically ignored by Git

### Step 4: Start the Development Server

Run the development server:
\`\`\`bash
npm run dev
\`\`\`

**Expected output**:
\`\`\`
  ▲ Next.js 16.0.0
  - Local:        http://localhost:3000
  - Environments: .env.local

✓ Ready in 2.1s
\`\`\`

### Step 5: Access the Application

1. Open your web browser
2. Navigate to: `http://localhost:3000`
3. You should see the OMDB Movie Explorer with the premium UI

## How to Use the Application

### Searching for Movies

1. Click on the search input field at the top of the page
2. Type a movie or TV series name (e.g., "Inception", "Breaking Bad")
3. Results will appear in real-time as you type
4. Click any result to view detailed information

### Viewing Movie Details

1. Click on any movie card or search result
2. A modal will open showing:
   - Movie poster and title
   - Plot summary
   - Cast information
   - IMDb rating
   - Release date
   - Runtime and genre
   - Other metadata

### Managing Favorites

1. Click the heart icon on any movie card to add to favorites
2. View all favorites by clicking the "Favorites" tab
3. Click the heart icon again to remove from favorites
4. Favorites are saved in your browser (localStorage)

### Using the Setup Guide

The app includes an interactive setup guide accessible from the interface that provides:
- Step-by-step instructions for configuration
- Environment variable setup help
- API key management tips
- Troubleshooting information

## Development Commands

\`\`\`bash
# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run linting checks
npm run lint
\`\`\`

## File Structure

\`\`\`
OMDB-Movie-Explorer/
├── app/
│   ├── api/
│   │   ├── search/
│   │   │   └── route.ts          # Movie search endpoint
│   │   └── movie/[id]/
│   │       └── route.ts           # Movie details endpoint
│   ├── page.tsx                   # Main page component
│   ├── layout.tsx                 # Root layout with fonts
│   ├── globals.css                # Global styles and design tokens
│   └── loading.tsx                # Loading state
├── components/
│   ├── animated-background.tsx    # Particle animation background
│   ├── movie-card.tsx             # Individual movie card
│   ├── movie-detail.tsx           # Movie detail modal
│   ├── movie-grid.tsx             # Grid layout component
│   ├── favorites-list.tsx         # Favorites display
│   └── step-guide.tsx             # Setup guide component
├── public/                        # Static assets
├── package.json                   # Project dependencies
├── tsconfig.json                  # TypeScript configuration
├── next.config.mjs                # Next.js configuration
└── .env.local                     # Environment variables (not in git)
\`\`\`

## API Endpoints

The application uses two main API endpoints:

### Search Movies
- **Endpoint**: `/api/search`
- **Method**: GET
- **Query Parameters**: 
  - `q` (required): Search query
  - `type` (optional): 'movie' or 'series'
- **Response**: Array of matching movies/series
- **Cache**: 5 minutes

### Get Movie Details
- **Endpoint**: `/api/movie/[id]`
- **Method**: GET
- **URL Parameters**:
  - `id` (required): OMDB ID (e.g., tt3896198)
- **Response**: Complete movie information
- **Cache**: 24 hours

## Caching System

The application implements an intelligent caching system:

- **Search Results**: Cached for 5 minutes, max 50 entries
- **Movie Details**: Cached for 24 hours, max 100 entries
- **Benefits**: 
  - Faster response times
  - Reduced API calls to OMDB
  - Lower bandwidth usage
  - Better user experience

## Troubleshooting

### Issue: "Invalid API key" Error

**Solution**:
1. Check that `OMDB_API_KEY` is set correctly in `.env.local`
2. Ensure the value is just the API key, not a full URL
3. Restart the development server after changing `.env.local`
4. Verify the API key is active (not expired)

### Issue: Port 3000 Already in Use

**Solution**:
\`\`\`bash
# Use a different port
npm run dev -- -p 3001
\`\`\`
Then access at `http://localhost:3001`

### Issue: Dependencies Installation Fails

**Solution**:
\`\`\`bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and package-lock.json
rm -rf node_modules package-lock.json

# Reinstall
npm install
\`\`\`

### Issue: Changes Not Reflecting

**Solution**:
1. Stop the development server (Ctrl+C)
2. Clear Next.js cache: `rm -rf .next`
3. Restart: `npm run dev`

## Building for Production

To create a production build:

\`\`\`bash
# Build the project
npm run build

# Start production server
npm start
\`\`\`

The build process will:
- Optimize all components
- Minimize CSS and JavaScript
- Pre-render static pages
- Create optimized output in `.next` folder

## Browser Support

The application works best on:
- Chrome/Chromium (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

Minimum required browser features:
- CSS Grid and Flexbox
- CSS Custom Properties
- ES6 JavaScript

## Performance Tips

1. **Use a wired internet connection** for best API response times
2. **Browser caching** is enabled for faster subsequent searches
3. **Lazy loading** of images for optimal performance
4. **Optimize network** by clearing browser cache if issues occur

## Getting Help

If you encounter issues:

1. **Check the console** for error messages (F12 in browser)
2. **Review `.env.local`** configuration
3. **Restart the server** after any changes
4. **Clear browser cache** (Ctrl+Shift+Delete)
5. **Try a different browser** to isolate issues

## Project Technologies

- **Framework**: Next.js 16 (App Router)
- **Runtime**: Node.js with TypeScript
- **Styling**: Tailwind CSS v4 with CSS custom properties
- **UI Components**: React 19 functional components
- **Animation**: CSS animations and transitions
- **Data Fetching**: Native fetch API with SWR-like patterns
- **API**: OMDB API (Open Movie Database)

## License

This project is provided as-is for educational and personal use.

## Support

For issues or questions:
1. Verify your setup matches these instructions
2. Check that all environment variables are correctly set
3. Ensure Node.js and npm are up to date
4. Try the troubleshooting section above

Enjoy exploring movies with the OMDB Movie Explorer!

<img width="1859" height="873" alt="Screenshot 2025-11-26 164656" src="https://github.com/user-attachments/assets/a634d81a-d8d2-4fa7-ab9e-f0b96a79c7fd" />

<img width="1861" height="962" alt="Screenshot 2025-11-26 163741" src="https://github.com/user-attachments/assets/95a8ed6d-ae66-419b-b2f9-7517511b19f7" />

