FROM node:16-alpine AS builder
WORKDIR /app
COPY . .
RUN npm install
ARG REACT_APP_BASEURL
ENV REACT_APP_BASEURL=$REACT_APP_BASEURL
RUN REACT_APP_BASEURL=$REACT_APP_BASEURL npm run build

FROM node:16-alpine AS final
WORKDIR /app
COPY --from=builder /app/build ./build
RUN npm install -g serve
EXPOSE 3000
CMD ["serve", "-s", "build", "-l", "3000"]