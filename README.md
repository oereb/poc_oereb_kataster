# poc_oereb_kataster

## Run

In oereb_stack:

```
mkdir -m 0777 ~/pgdata
```

```
docker-compose up
```

In oereb_gretljobs:
```
export ORG_GRADLE_PROJECT_dbUriOerebV2="jdbc:postgresql://oereb-db/oereb"
export ORG_GRADLE_PROJECT_dbUserOerebV2="gretl"
export ORG_GRADLE_PROJECT_dbPwdOerebV2="gretl"
```

```
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/oereb_av replaceCadastralSurveyingData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/oereb_plzo importPLZO
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/ch/oereb_bundesgesetze importData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/ch/oereb_bundeskonfiguration importBundeskonfiguration

./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/so/oereb_kantonskonfiguration importKantonskonfiguration

```


oereb_bundesgesetze:importData :oereb_bundeskonfiguration:importBundeskonfiguration