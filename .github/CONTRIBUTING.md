# ✨ Contributing to OpenCut

Thank you for your interest in contributing to **OpenCut** — a free, open-source video editor for web, desktop, and mobile!

This guide provides everything you need to get started, set up the project locally, and contribute confidently — even as a beginner. 🎉

---

## 🚀 Getting Started

1. **Fork** the repository to your GitHub account
2. **Clone** your fork locally
3. Navigate to the web app directory:

   ```bash
   cd apps/web

4. Install dependencies: `bun install`
5. Start the development server: `bun run dev`
Note: If you see an error like Unsupported URL Type "workspace:*" when using npm install, either:

Upgrade to npm v9 or higher (supports workspace protocol), or

Use an alternative like bun or pnpm.

> **Note:** If you see an error like `Unsupported URL Type "workspace:*"` when running `npm install`, you have two options:
>
> 1. Upgrade to a recent npm version (v9 or later), which has full workspace protocol support.
> 2. Use an alternative package manager such as **bun** or **pnpm**.

🛠 Development Setup
✅ Prerequisites
Node.js 18+

Bun (latest version)

Docker + Docker Compose

### Local Development

1. Start the database and Redis services:

   ```bash
   # From project root
   docker-compose up -d
   ```

2. Navigate to the web app directory:

   ```bash
   cd apps/web
   ```

3. Copy `.env.example` to `.env.local`:

   ```bash
   # Unix/Linux/Mac
   cp .env.example .env.local

   # Windows Command Prompt
   copy .env.example .env.local

   # Windows PowerShell
   Copy-Item .env.example .env.local
   ```

4. Configure required environment variables in `.env.local`:

   **Required Variables:**

   ```bash
   # Database (matches docker-compose.yaml)
   DATABASE_URL="postgresql://opencut:opencutthegoat@localhost:5432/opencut"

   # Generate a secure secret for Better Auth
   BETTER_AUTH_SECRET="your-generated-secret-here"
   BETTER_AUTH_URL="http://localhost:3000"

   # Redis (matches docker-compose.yaml)
   UPSTASH_REDIS_REST_URL="http://localhost:8079"
   UPSTASH_REDIS_REST_TOKEN="example_token"

   # Development
   NODE_ENV="development"
   ```

   **Generate BETTER_AUTH_SECRET:**

   ```bash
   # Unix/Linux/Mac
   openssl rand -base64 32

   # Windows PowerShell (simple method)
   [System.Web.Security.Membership]::GeneratePassword(32, 0)

   # Cross-platform (using Node.js)
   node -e "console.log(require('crypto').randomBytes(32).toString('base64'))"

   # Or use an online generator: https://generate-secret.vercel.app/32
   ```

   **Optional Variables (for Google OAuth):**

   ```bash
   # Only needed if you want to test Google login
   GOOGLE_CLIENT_ID="your-google-client-id"
   GOOGLE_CLIENT_SECRET="your-google-client-secret"
   ```

5. Run database migrations: `bun run db:migrate`
6. Start the development server: `bun run dev`

🤝 How to Contribute
🐞 Report Bugs
Use the bug report template

Include steps to reproduce

Add screenshots if possible

💡 Suggest Features
Use the feature request template

Clearly describe the use case and value
👨‍💻 Code Contributions

1. Create a new branch: `git checkout -b feature/your-feature-name`
2. Make your changes
3. Navigate to the web app directory: `cd apps/web`
4. Run the linter: `bun run lint`
5. Format your code: `bunx biome format --write .`
6. Commit your changes with a descriptive message
7. Push to your fork and create a pull request

🎨 Code Style

- We use Biome for code formatting and linting
- Run `bunx biome format --write .` from the `apps/web` directory to format code
- Run `bun run lint` from the `apps/web` directory to check for linting issues
- Follow the existing code patterns

📦 Pull Request Process
Fill out the PR template clearly

Link to any related issues (Closes #123)

Ensure CI checks pass

Request a review

Address all feedback kindly
🌟 Community Guidelines
Be respectful and helpful

Follow the Code of Conduct

Support others in issues & discussions
