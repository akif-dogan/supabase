FROM kong/kong:3.9.1

# Embed entrypoint + declarative config inside the image so we don't depend
# on Coolify-controlled bind mounts (which had path-resolution issues with
# our deployment artifact layout).
USER root
COPY kong-entrypoint.sh /home/kong/kong-entrypoint.sh
COPY kong.yml /home/kong/temp.yml
RUN chmod +x /home/kong/kong-entrypoint.sh && \
    chown kong:kong /home/kong/kong-entrypoint.sh /home/kong/temp.yml

USER kong
ENTRYPOINT ["/home/kong/kong-entrypoint.sh"]
