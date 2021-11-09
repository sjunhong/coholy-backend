# dnd-mentee-4th-5-backend

![](coverage.svg)

## Introduction

Coholy, drinking review app backend repo

<br>

## Project Structure
We have applied DDD (Domain Driven Design) architecture.
Divided packages in Domain level and divided Domains into Layers.
Package structure looks like
```
.
└── app
    ├── auth
    │   ├── application
    │   ├── domain
    │   └── external_interface
    ├── drinks
    │   ├── application
    │   ├── domain
    │   ├── external_interface
    │   └── infra_structure
    ├── health
    │   └── external_interface
    ├── reviews
    │   ├── application
    │   ├── domain
    │   ├── external_interface
    │   └── infra_structure
    ├── shared_kernel
    │   ├── application
    │   ├── domain
    │   ├── external_interface
    │   └── infra_structure
    ├── users
    │   ├── application
    │   ├── domain
    │   ├── external_interface
    │   └── infra_structure
    └── wishes
        ├── application
        ├── domain
        ├── external_interface
        └── infra_structure
└── tests
```

And here is example of how each layer looks like

```
.
├── application
│   ├── dtos.py
│   └── service.py
├── domain
│   ├── entities.py
│   ├── repository.py
│   └── value_objects.py
├── external_interface
│   ├── json_dtos.py
│   └── routers.py
└── infra_structure
    ├── in_memory_repository.py
    ├── orm_models.py
    └── orm_repository.py

```

<br>

## How to Install

```bash
$ git clone https://github.com/dnd-mentee-4th/dnd-mentee-4th-5-backend.git
...

$ cd dnd-mentee-4th-5-backend.git
$ poetry install
```

<br>

## How to Run or Deploy

### Local Environment

To run, please set up environment variables

```
JWT_SECRET_KEY = {SECRET KEY for JWT} 
JWT_ALGORITHM = {name of hash algorithm for JWT}
DB_URL = {SQLALCHEMY CONNECTION URL of Postgres DB}
TEST_DB_URL = {SQLALCHEMY CONNECTION URL of Postgres DB for Test Purpose}
```

For example

```
JWT_SECRET_KEY = "09d25e094faa6ca2556c818166b7a9563b93f7099f6f0f4caa6cf63b88e8d3e7"
JWT_ALGORITHM = "HS256"
DB_URL = "postgresql://root:1234@localhost:5432/coholy"
TEST_DB_URL = "postgresql://root:1234@localhost:5432/coholy_test"
```

Example using `python` command.

```bash
$ python app/main.py
```

### Docker

After `docker` build, use Docker Container to run.

```bash
$ docker build -t coholy-backend-server .
$ docker run -d -p 8080:8080 \
-e JWT_SECRET_KEY = {SECRET KEY for JWT}   \
-e JWT_ALGORITHM = {name of hash algorithm for JWT} \
-e DB_URL = {SQLALCHEMY CONNECTION URL of Postgres DB} \
coholy-backend-server 
```

<br>

---

## Coding and Versioning Convention

### Package Dependencies 

In development, use [poetry](https://github.com/python-poetry/poetry)for package manager.
In Production, use `pip` and `requirements.txt`.

```bash
# after git clone, install dependencies
$ poetry install

# when adding packages.
$ poetry add pandas
$ poetry add pytest -D  # -D option for development dependencies

# When requirements.txt is needed
$ poetry export -o requirements.txt --without-hashes
```

<br>

### Git Commit

follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

```
fix: A bug fix. Correlates with PATCH in SemVer
feat: A new feature. Correlates with MINOR in SemVer
docs: Documentation only changes
style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
refactor: A code change that neither fixes a bug nor adds a feature
perf: A code change that improves performance
test: Adding missing or correcting existing tests
build: Changes that affect the build system or external dependencies (example scopes: pip, docker, npm)
ci: Changes to our CI configuration files and scripts (example scopes: GitLabCI)
```

for commit, do not use `git commit`. Instead use [commitizen](https://github.com/commitizen-tools/commitizen).

```bash
$ poetry shell

# example of commitzen
$ (.venv) cz c
? Select the type of change you are committing  build: Changes that affect the build system or external dependencies (example scopes: pip, docker, npm)
? What is the scope of this change? (class or file name): (press [enter] to skip)

? Write a short and imperative summary of the code changes: (lower case and no period)
 added packages
? Provide additional contextual information about the code changes: (press [enter] to skip)

? Is this a BREAKING CHANGE? Correlates with MAJOR in SemVer  No
? Footer. Information about Breaking Changes and reference issues that this commit closes: (press [enter] to skip)

build: added packages
```

Use `git log` to check.

```bash
$ (.venv) git log --oneline

b3929f1 (HEAD -> main) build: added packages
d55aa6a (origin/main, origin/HEAD) template update: ISSUE + PR (#2)
56b13b1 Initial commit
```

<br>

### Git Branch

```
main: Code for production
develop: Not in production, code for future versions. 
feature: From develop brank, code for individual features. 
```

Especially, name of `feature` branch should be in the form `feature/issue-number/task-name`
for example, `feature/3/auth`.

example of work flow

```bash
$ git switch develop
$ git switch -c feature/3/auth

writing codes and commits

$ git push origin feature/3/auth
```

### Pull Request

Pull Request, Merge works in Github.

- content of PR should be in Issue. If it is not in Issue, please make one.
- Use Template for PR submission.
- After creating PR, add corresponding issue to Linked issued.
- `feature` -> `develop` Merge: `Squash & Merge`.
- `develop` -> `main` Merge: `Merge commits`.

Flow of Pull Request, Merge: `feature` -> `develop` -> `main`.

<br>

---

## Team

| Parts         | Name           |
| ------------- | ---------------|
| Backend.      | Si Heum Jeon   |
| Backend       | Seok Jun Hong  |
| Frontend      | Da Ye Lee      |
| Frontend      | Dong Young Kim |
| Design        | Ye Na Lee.     |
| Design        | So Eun Choi.   |

<br>

## links

- [frontend](https://github.com/dnd-mentee-4th/dnd-mentee-4th-5-frontend)
- [backend](https://github.com/dnd-mentee-4th/dnd-mentee-4th-5-backend)
- [team Notion](https://www.notion.so/330adbd74609421e89a9473e84a8204f)
