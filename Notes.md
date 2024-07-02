## DB
- Delete runner data
```cmd
$  docker compose exec -it db psql -U gitea -W gitea
$  psql> DELETE FROM "public"."action_runner"
```
## Runner
1 - Create Config:

```cmd
$ docker run --entrypoint="" --rm -it gitea/act_runner:0.2.10 act_runner generate-config > config.yaml
```

2 - If failed delete .runner file

```cmd
$ docker run --rm -it --entrypoint bash gitea/act_runner:0.2.10

$ rm -rf ./.runner
```

if it registered correctly, it prints:

```cmd
$ .runner is missing or not a regular file
$ level=info msg="Registering runner, arch=amd64, os=linux, version=v0.2.10."
$ level=debug msg="Successfully pinged the Gitea instance server"
$ level=info msg="Runner registered successfully."
$ SUCCESS
$ time="2024-07-02T18:09:05Z" level=info msg="Starting runner daemon"
$ time="2024-07-02T18:09:05Z" level=info msg="runner: 93d5349a57fa, with version: v0.2.10, with labels: [ubuntu-latest ubuntu-22.04 ubuntu-20.04], declare successfully"

```