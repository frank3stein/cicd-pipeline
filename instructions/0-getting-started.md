## Getting Started

Instructions for how to get a copy of the project running on your local machine.

### Dependencies

NodeJs v10 or higher

### Starter Code
1. Clone the [starter code](https://github.com/udacity/cdond-c3-projectstarter) to your machine so that you can manipulate the files.
2. Push your code into a repository in your account in Github.

### Provided Cloud Formation Templates

For your convenience, we have provided some CloudFormation templates that you can use throughout the deployment phase of your project. You can find those templates in [this folder](https://github.com/udacity/cdond-c3-projectstarter/tree/master/.circleci/files). 

### Installation

This is a "mono-repository" which means multiple servers or layers exist in the same repository. You'll find the following main folders:

- `./frontend`
- `./backend`

#### 1. Install dependencies in both front-end and back-end folders.

```bash
cd frontend
npm i
```

```bash
cd backend
npm i
```

#### 2. Create `.env` file for database connection info.

Add a `.env` file to your `backend` folder with the following contents:

```bash
NODE_ENV=local
VERSION=1
TYPEORM_CONNECTION=postgres
TYPEORM_MIGRATIONS_DIR=./src/migrations
TYPEORM_ENTITIES=./src/modules/domain/**/*.entity.ts
TYPEORM_MIGRATIONS=./src/migrations/*.ts

# Things you can change if you wish...
TYPEORM_HOST=localhost
TYPEORM_PORT=5532
TYPEORM_USERNAME=postgres
TYPEORM_PASSWORD=password
TYPEORM_DATABASE=glee
```

You can use your own Postgres server if you wish or you can use the Docker-Compose template we provided in the `./utils` folder.

## Running PostgreSQL in Docker-Compose

For convenience, we have provided a template that you can use to easily run a Postgres database for local testing. To run this template, you'll need to install Docker and Docker-Compose.

To start the database:

```bash
cd utils
docker-compose up
```

## Compiling the Code

You can compile the code from the command-line using the following:

```bash
cd frontend
npm run build
```

```bash
cd backend
npm run build
```

**WARNING:** There are some errors in both front-end and back-end that will make any attempt to compile FAIL when you first clone the repo. These errors are **intentional**. There are steps in the project that require a build to break in Circle CI. Please don't fix these errors until instructed to do so later on.

## Testing, Migrating, Running

As the warning says above, it won't be possible to run most of the code in the project until later on when instructed to fix some errors. So, you may not be able to try these things out right now. But we are providing them here as a reference.

Most of the tasks needed to build, test and deploy the application are simplified by "npm scripts" that are found in the `package.json` for either front-end or back-end. For any of these scripts, you will need to `cd` into the respective folder and then run the script using the command `npm run [script name]`. Here are the most relevant scripts:

| Name | Purpose | Notes | 
| :-- | :-- | :-- |
| migrate | Run migration which checks for any migration scripts that have not yet been applied to the db and runs them. |Make sure you have a Postgres database running and your `.env` file is configured correctly. If you get connection errors from the backend when you start it, then chances are your DB is not running or the `.env` doesn't have the correct DB connection information. |
| test | Run all unit tests. | |
| build | Compiles the code. | Drops the compiled code in the `./dist` folder. |
| start | Starts up the application locally. | Make sure you have a Postgres database running and your `.env` file is configured correctly. If you get connection errors from the backend when you start it, then chances are your DB is not running or the `.env` doesn't have the correct DB connection information.|

Example:
```bash
cd frontend
npm run build
cd dist
ls
```

This should compile the code and then list the result in the `./dist` folder.