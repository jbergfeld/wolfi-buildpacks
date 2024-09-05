# Base stack using Wolfi

FROM cgr.dev/chainguard/wolfi-base

ARG cnb_uid=1000
ARG cnb_gid=1000
ENV CNB_USER_ID=${cnb_uid}
ENV CNB_GROUP_ID=${cnb_gid}

RUN addgroup -S cnb -g ${CNB_GROUP_ID}
RUN adduser -S -G cnb cnb -u ${CNB_USER_ID}
# needed for npm
RUN apk update && apk add libstdc++

USER cnb

CMD ["/bin/sh"]

# Buildpack metadata
ENV CNB_STACK_ID="io.buildpacks.stacks.wolfi"
LABEL io.buildpacks.base.distro.name="io.buildpacks.stacks.wolfi"
LABEL io.buildpacks.base.distro.version="1.0"

