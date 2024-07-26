# Etapa de construcción
FROM dart:stable AS build

WORKDIR /unpub
COPY . .

RUN dart pub get
RUN dart compile exe bin/unpub.dart -o bin/server

# Etapa de producción
FROM debian:buster-slim
WORKDIR /unpub
COPY --from=build /runtime/ /
COPY --from=build /unpub/bin/server ./bin/server

CMD ["./bin/server"]
