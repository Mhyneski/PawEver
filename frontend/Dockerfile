# 1. Use official Node.js image
FROM node:20-alpine AS builder

# 2. Set working directory
WORKDIR /app

# 3. Copy package.json and package-lock.json first (for caching)
COPY package*.json ./

# 4. Install dependencies
RUN npm install --frozen-lockfile

# 5. Copy the rest of your code
COPY . .

# 6. Build the Next.js app
RUN npm run build

# 7. Production image
FROM node:20-alpine AS runner

WORKDIR /app

# Set NODE_ENV to production
ENV NODE_ENV=production

# Copy only the necessary files from the builder
COPY --from=builder /app/package*.json ./
COPY --from=builder /app/.next ./.next
COPY --from=builder /app/public ./public
COPY --from=builder /app/node_modules ./node_modules

EXPOSE 3000

# Start Next.js
CMD ["npm", "start"]