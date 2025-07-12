✨ Contributing to OpenCut
Thank you for your interest in contributing to OpenCut — a free and open-source video editor built for web, desktop, and mobile.

This guide will walk you through how to get started, set up the project, and make meaningful contributions. Whether you're fixing a typo or adding new features, you're welcome here! 💙

🚀 Getting Started
Fork the repository to your GitHub account.

Clone your fork locally.

Navigate to the web app directory:

bash
Copy
Edit
cd apps/web
Install dependencies:

bash
Copy
Edit
bun install
Start the development server:

bash
Copy
Edit
bun run dev
💡 Note: If you get an error like Unsupported URL Type "workspace:*" when running npm install, you have two options:

Upgrade to npm v9+, which supports workspace protocols.

Use an alternative package manager like bun or pnpm.

🧰 Development Setup
✅ Prerequisites
Node.js 18+

Bun (latest version)

Docker (for running Postgres & Redis locally)

⚙️ Local Development
Start backend services using Docker:

bash
Copy
Edit
# From the project root
docker-compose up -d
Navigate to the web app directory:

bash
Copy
Edit
cd apps/web
Copy environment variables file:

bash
Copy
Edit
# Unix/Linux/Mac
cp .env.example .env.local

# Windows (CMD)
copy .env.example .env.local

# Windows (PowerShell)
Copy-Item .env.example .env.local
Edit .env.local and update the required variables:

env
Copy
Edit
DATABASE_URL="postgresql://opencut:opencutthegoat@localhost:5432/opencut"
BETTER_AUTH_SECRET="your-generated-secret-here"
BETTER_AUTH_URL="http://localhost:3000"
UPSTASH_REDIS_REST_URL="http://localhost:8079"
UPSTASH_REDIS_REST_TOKEN="example_token"
NODE_ENV="development"
Generate a secure auth secret:

bash
Copy
Edit
# Unix/Linux/Mac
openssl rand -base64 32

# Windows (PowerShell)
[System.Web.Security.Membership]::GeneratePassword(32, 0)

# Node.js (cross-platform)
node -e "console.log(require('crypto').randomBytes(32).toString('base64'))"
Or use an online generator: https://generate-secret.vercel.app/32

Run database migrations:

bash
Copy
Edit
bun run db:migrate
Start the development server:

bash
Copy
Edit
bun run dev
💡 If you're using Windows and face issues with paths, try using Git Bash or WSL for better compatibility.

🤝 How to Contribute
🐞 Reporting Bugs
Use the bug report template

Include clear steps to reproduce

Provide screenshots or error logs if helpful

💡 Suggesting Features
Use the feature request template

Describe the use case clearly

Share any relevant implementation ideas

👨‍💻 Code Contributions
Create a new branch:

bash
Copy
Edit
git checkout -b feature/your-feature-name
Make your changes.

Run the linter:

bash
Copy
Edit
bun run lint
Format the code:

bash
Copy
Edit
bunx biome format --write .
Commit with a clear message:

bash
Copy
Edit
git commit -m "feat: add new video trimming feature"
Push to your fork and open a pull request.

🎨 Code Style
We use Biome for formatting and linting.

From the apps/web directory, run:

bash
Copy
Edit
bunx biome format --write .
bun run lint
Follow the existing code patterns and structure.

Keep functions modular and components reusable.

🔁 Pull Request Process
Fill out the pull request template completely.

Link to any related issues (e.g., Closes #123).

Make sure CI passes.

Request a review from a maintainer.

Address any feedback respectfully and promptly.

🌍 Community Guidelines
We believe in a friendly, inclusive, and supportive community. 💬

Be kind, respectful, and open to learning.

Follow our Code of Conduct.

Help others in issues or discussions if you can.

🙏 Thank You!
Your contribution — big or small — means a lot to the OpenCut project. 💖
Whether you're fixing typos, building features, or helping others, you're making this better for everyone.

Welcome to the team! 🚀
