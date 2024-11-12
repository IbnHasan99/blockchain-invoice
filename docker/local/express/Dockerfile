ARG NODE_VERSION=20-alpine3.20

FROM  node:${NODE_VERSION}

LABEL name="blockchain-invoice"
LABEL license="MIT"
LABEL description="Blockchain Invoice"

ENV NODE_ENV=development

ARG APP_HOME=/app

WORKDIR ${APP_HOME}

RUN addgroup --system blockchain-invoice
RUN adduser --system --ingroup blockchain-invoice myuser

RUN apk --update add ttf-freefont fontconfig && rm -rf /var/cache/apk/*

COPY package*.json ./

RUN npm install

COPY --chown=myuser:blockchain-invoice . ${APP_HOME}

RUN chown myuser:blockchain-invoice ${APP_HOME}

USER myuser

CMD ["npm", "run", "dev"]

