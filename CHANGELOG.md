CHANGELOG
=========

v2.0.2 (06.04.2021)
-------------------
- 🐛 Fix: Bug with required Root CA certificate for the SSL, not it's optional.
- 🆕 New: HTTP/FCGI/HTTPS internal logs instead of going to the raw stdout will be displayed in the RR logger at the `Info` log level.

v2.0.1 (09.03.2021)
-------------------
- 🐛 Fix: incorrect PHP command validation
- 🐛 Fix: ldflags properly inject RR version
- ⬆️ Update: README, links to the go.pkg from v1 to v2
- 📦 Bump golang version in the Dockerfile and in the `go.mod` to 1.16
- 📦 Bump Endure container to v1.0.0.


v2.0.0 (02.03.2021)
-------------------

- ✔️ Add a shared server to create PHP worker pools instead of isolated worker pool in each individual plugin.
- 🆕 New plugin system with auto-recovery, easier plugin API.
- 📜 New `logger` plugin to configure logging for each plugin individually.
- 🔝 Up to 50% performance increase in HTTP workloads.
- ✔️ Add **[Temporal Workflow](https://temporal.io)** plugin to run distributed computations on scale.
- ✔️ Add `debug` flag to reload PHP worker ahead of a request (emulates PHP-FPM behavior).
- ❌ Eliminate `limit` service, now each worker pool includes `supervisor` configuration.
- 🆕 New resetter, informer plugins to perform hot reloads and observe loggers in a system.
- 💫 Expose more HTTP plugin configuration options.
- 🆕 Headers, static and gzip services now located in HTTP config.
- 🆕 Ability to configure the middleware sequence.
- 💣 Faster Goridge protocol (eliminated 50% of syscalls).
- 💾 Add support for binary payloads for RPC (`msgpack`).
- 🆕 Server no longer stops when a PHP worker dies (attempts to restart).
- 💾 New RR binary server downloader.
- 💣 Echoing no longer breaks execution (yay!).
- 🆕 Migration to ZapLogger instead of Logrus.
- 💥 RR can no longer stuck when studding down with broken tasks in a pipeline.
- 🧪 More tests, more static analysis.
- 💥 Create a new foundation for new KV, WebSocket, GRPC and Queue plugins.

v2.0.0-RC.4 (20.02.2021)
-------------------

- PHP tests use latest signatures (https://github.com/spiral/roadrunner/pull/550).
- Endure container update to v1.0.0-RC.2 version.
- Remove unneeded mutex from the `http.Workers` method.
- Rename `checker` plugin package to `status`, remove `/v1` endpoint prefix (#557).
- Add static, headers, status, gzip plugins to the `main.go`.
- Fix workers pool behavior -> idle_ttl, ttl, max_memory are soft errors and exec_ttl is hard error.

v2.0.0-RC.3 (17.02.2021)
-------------------

- Add support for the overwriting `.rr.yaml` keys with values (ref: https://roadrunner.dev/docs/intro-config)
- Make logger plugin optional to define in the config. Default values: level -> `debug`, mode -> `development`
- Add the ability to read env variables from the `.rr.yaml` in the form of: `rpc.listen: {RPC_ADDR}`. Reference:
  ref: https://roadrunner.dev/docs/intro-config (Environment Variables paragraph)

v2.0.0-RC.2 (11.02.2021)
-------------------

- Update RR to version v2.0.0-RC.2
- Update Temporal plugin to version v2.0.0-RC.1
- Update Goridge to version v3.0.1
- Update Endure to version v1.0.0-RC.1
