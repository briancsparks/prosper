---
title: "Nodejs Dockerfile"
date: 2020-04-11T14:19:35-07:00
draft: false
weight: 2
---

### Canonical Node Dockerfile Pattern

The trick is to copy only the `package.json` file, and then `npm install`, so that the huge
`node_modules` directory (which doesn't change often) is early in the process and chached.
Then, copy our (constantly changing) source.

```dockerfile
FROM node:12-stretch-slim
WORKDIR /work/src

#COPY package.json yarn* ./
COPY package.json package-lock*.json ./

RUN npm install --only production

COPY . .
```
