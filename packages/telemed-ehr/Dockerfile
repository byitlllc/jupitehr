FROM node:18-alpine AS base

ARG NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY
ARG CLERK_SECRET_KEY
# ARG NEXT_PUBLIC_STORAGESASTOKEN
# ARG NEXT_PUBLIC_STORAGERESOURCENAME
ARG SENTRY_AUTH_TOKEN
# ARG NEXT_PUBLIC_API_URL
# ARG NEXT_PUBLIC_MANAGE_USER_FUNCTION_BASE_URL

# 1. Install dependencies only when needed
FROM base AS deps
# Check https://github.com/nodejs/docker-node/tree/b4117f9333da4138b03a546ec926ef50a31506c3#nodealpine to understand why libc6-compat might be needed.
RUN apk add --no-cache libc6-compat

WORKDIR /app

# Install dependencies based on the preferred package manager
COPY ./app ./app
COPY ./zambdas ./zambdas

RUN cd ./app && npm install

RUN ls -la


# RUN cd ./app && npm run build:production

RUN ls -la

# RUN yarn --frozen-lockfile --verbose
# RUN yarn --frozen-lockfile