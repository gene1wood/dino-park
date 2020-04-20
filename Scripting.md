# Automation

We use [myke] (actually the [rust version of myke]) for basic automation instead of
make or shell scripts. It utilizes golang templating like helm which allows us to only
use one templating language. Look into the `myke.yaml` in any repository file to see
how it works.

```bash
$ myke

 PROJECT         | TAGS | TASKS
-----------------+------+-------------------------------
 dino-park-fence |      | compile-release, deploy,
                 |      | docker, docker-local,
                 |      | package, package-local,
                 |      | push-image, run-dev

```
