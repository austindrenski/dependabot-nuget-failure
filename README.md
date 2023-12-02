# Dependabot fails on NuGet updates with `file_fetcher_error`

## Minimal reproduction

- https://github.com/austindrenski/dependabot-nuget-failure/network/updates/757428563

```
  proxy | 2023/12/02 00:17:24 proxy starting, commit: 6cffd6fae1b2f713f2d837bc45fe916f855c821d
  proxy | 2023/12/02 00:17:24 Listening (:1080)
updater | 2023-12-02T00:17:25.267021840 [757428563:main:WARN:src/devices/src/legacy/serial.rs:222] Detached the serial input due to peer close/error.
updater | time="2023-12-02T00:17:27Z" level=info msg="guest starting" commit=17df297b9449ef5936111b658329653bcfc0c9bc
updater | time="2023-12-02T00:17:27Z" level=info msg="starting job..." fetcher_timeout=10m0s job_id=757428563 updater_timeout=45m0s updater_version=ad73cc6aa16e85e1a2f46ede0b3cf7eb5dac4e3c-nuget
updater | 2023/12/02 00:17:29 INFO Raven 3.1.2 ready to catch errors
updater | 2023/12/02 00:17:32 INFO <job_757428563> Starting job processing
  proxy | 2023/12/02 00:17:32 [002] GET https://github.com:443/austindrenski/dependabot-nuget-failure/info/refs?service=git-upload-pack
  proxy | 2023/12/02 00:17:32 [002] * authenticating git server request (host: github.com)
  proxy | 2023/12/02 00:17:32 [002] 200 https://github.com:443/austindrenski/dependabot-nuget-failure/info/refs?service=git-upload-pack
  proxy | 2023/12/02 00:17:32 [003] POST https://github.com:443/austindrenski/dependabot-nuget-failure/git-upload-pack
  proxy | 2023/12/02 00:17:32 [003] * authenticating git server request (host: github.com)
  proxy | 2023/12/02 00:17:32 [003] 200 https://github.com:443/austindrenski/dependabot-nuget-failure/git-upload-pack
  proxy | 2023/12/02 00:17:32 [004] POST https://github.com:443/austindrenski/dependabot-nuget-failure/git-upload-pack
  proxy | 2023/12/02 00:17:32 [004] * authenticating git server request (host: github.com)
  proxy | 2023/12/02 00:17:32 [004] 200 https://github.com:443/austindrenski/dependabot-nuget-failure/git-upload-pack
updater | 2023/12/02 00:17:32 ERROR <job_757428563> Error during file fetching; aborting: no implicit conversion of nil into String
updater | 2023/12/02 00:17:32 ERROR <job_757428563> no implicit conversion of nil into String
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/nuget/lib/dependabot/nuget/file_fetcher.rb:48:in `join'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/nuget/lib/dependabot/nuget/file_fetcher.rb:48:in `block in fetch_files'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/nuget/lib/dependabot/nuget/file_fetcher.rb:47:in `uniq'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/nuget/lib/dependabot/nuget/file_fetcher.rb:47:in `fetch_files'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/vendor/ruby/3.1.0/gems/sorbet-runtime-0.5.11142/lib/types/private/methods/call_validation.rb:256:in `bind_call'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/vendor/ruby/3.1.0/gems/sorbet-runtime-0.5.11142/lib/types/private/methods/call_validation.rb:256:in `validate_call'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/vendor/ruby/3.1.0/gems/sorbet-runtime-0.5.11142/lib/types/private/methods/_methods.rb:275:in `block in _on_method_added'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/common/lib/dependabot/file_fetchers/base.rb:108:in `files'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/vendor/ruby/3.1.0/gems/sorbet-runtime-0.5.11142/lib/types/private/methods/call_validation.rb:256:in `bind_call'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/vendor/ruby/3.1.0/gems/sorbet-runtime-0.5.11142/lib/types/private/methods/call_validation.rb:256:in `validate_call'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/vendor/ruby/3.1.0/gems/sorbet-runtime-0.5.11142/lib/types/private/methods/_methods.rb:275:in `block in _on_method_added'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/lib/dependabot/file_fetcher_command.rb:107:in `block in dependency_files'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/lib/dependabot/file_fetcher_command.rb:125:in `with_retries'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/lib/dependabot/file_fetcher_command.rb:107:in `dependency_files'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/lib/dependabot/file_fetcher_command.rb:30:in `perform_job'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> /home/dependabot/dependabot-updater/lib/dependabot/base_command.rb:53:in `run'
updater | 2023/12/02 00:17:32 ERROR <job_757428563> bin/fetch_files.rb:24:in `<main>'
updater | 2023/12/02 00:17:32 INFO <job_757428563> Sending event 16e6ff5f1320461c8b451e099971695a to Sentry
  proxy | 2023/12/02 00:17:33 [006] POST https://sentry.io:443/api/1451818/store/
  proxy | 2023/12/02 00:17:33 [006] 200 https://sentry.io:443/api/1451818/store/
updater | 2023/12/02 00:17:33 INFO <job_757428563> Finished job processing
updater | 2023/12/02 00:17:33 INFO Results:
updater | Dependabot encountered '1' error(s) during execution, please check the logs for more details.
updater | +--------------------+
updater | |       Errors       |
updater | +--------------------+
updater | | file_fetcher_error |
updater | +--------------------+
updater | time="2023-12-02T00:17:33Z" level=info msg="task complete" container_id=job-757428563-file-fetcher exit_code=0 job_id=757428563 step=fetcher
updater | time="2023-12-02T00:17:34Z" level=warning msg="failed during fetch, skipping updater" job_id=757428563
```
