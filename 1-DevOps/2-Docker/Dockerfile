FROM node:20-alpine AS deps

RUN apk add --no-cache libc6-compat
WORKDIR /app
RUN corepack enable
COPY package.json .
COPY yarn.lock .
COPY .yarnrc.yml .
RUN yarn install --immutable


FROM node:20-alpine
RUN corepack enable
ARG NEXT_PUBLIC_ENABLE_IDEM_FORM=false
ARG NEXT_PUBLIC_SHOW_SEEDED_IDEMS=false
COPY node_modules .
COPY .yarn .
COPY . .
RUN yarn build