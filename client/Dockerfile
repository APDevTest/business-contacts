
# FROM node

# WORKDIR /app

# COPY . .

# RUN npm install && npm run build

# EXPOSE 1234

# CMD ["node", "server.js"]

# ---- Base Node ----
    FROM node AS base
    WORKDIR /app
    COPY . .
    
    # ---- Dependencies ----
    FROM base AS dependencies
    RUN npm install && npm run build
    
    # ---- Release ----
    FROM node AS release
    WORKDIR /app
    COPY --from=dependencies /app .
    RUN npm install -g parcel-bundler && npm install --only=production
    EXPOSE 1234
    CMD ["npm", "start"]