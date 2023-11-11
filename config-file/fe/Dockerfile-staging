FROM node:16-alpine AS builder
WORKDIR /app
COPY . .
RUN npm install
ARG REACT_APP_BASEURL
ENV REACT_APP_BASEURL=$REACT_APP_BASEURL
RUN REACT_APP_BASEURL=$REACT_APP_BASEURL npm run build

FROM nginx:alpine AS final
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]