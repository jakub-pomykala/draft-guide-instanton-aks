# tag::kernel-slim[]
FROM icr.io/appcafe/open-liberty:kernel-slim-java17-openj9-ubi
# end::kernel-slim[]


ARG VERSION=1.0
ARG REVISION=SNAPSHOT

LABEL \
  org.opencontainers.image.authors="Your Name" \
  org.opencontainers.image.vendor="Open Liberty" \
  org.opencontainers.image.url="local" \
  org.opencontainers.image.source="https://github.com/OpenLiberty/guide-cloud-azure" \
  org.opencontainers.image.version="$VERSION" \
  org.opencontainers.image.revision="$REVISION" \
  vendor="Open Liberty" \
  name="system" \
  version="$VERSION-$REVISION" \
  summary="The system microservice from the Deploying microservices to Azure Kubernetes Service guide" \
  description="This image contains the system microservice running with the Open Liberty runtime."

# tag::config[]
COPY --chown=1001:0 src/main/liberty/config/ /config/
# end::config[]
# tag::features[]
RUN features.sh
# end::features[]
# tag::war[]
COPY --chown=1001:0 target/guide-instanton-aks.war /config/apps
# end::war[]
# tag::configure[]
RUN configure.sh
# end::configure[]

# tag::checkpoint[]
RUN checkpoint.sh afterAppStart
# end::checkpoint[]