# Multi-stage build for static website
# Stage 1: Base image with nginx
FROM nginx:alpine

# Set working directory
WORKDIR /usr/share/nginx/html/

# Remove default nginx config
RUN rm -rf /etc/nginx/conf.d/default.conf

# Copy custom nginx configuration (optional - for production)
# COPY nginx.conf /etc/nginx/conf.d/

# Copy all static files from Website folder to nginx html directory
COPY . .

# Expose port 80 for HTTP traffic
EXPOSE 80

# Health check to verify container is working
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD wget --quiet --tries=1 --spider http://localhost/ || exit 1

# Start nginx in foreground (required for containers)
CMD ["nginx", "-g", "daemon off;"]

# Labels for image metadata
LABEL maintainer="DevOps Team"
LABEL description="Static website container with nginx"
LABEL version="1.0"