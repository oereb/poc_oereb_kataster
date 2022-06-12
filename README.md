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
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/sh/oereb_kantonskonfiguration importKantonskonfiguration
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/so/oereb_kantonskonfiguration importKantonskonfiguration
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/sz/oereb_kantonskonfiguration importKantonskonfiguration
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/ch/oereb_bundesdaten importData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/sh/oereb_kbs importData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/so/oereb_kbs importData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/so/oereb_grundwasserschutz importData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/so/oereb_nutzungsplanung importData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/so/oereb_nutzungsplanung_kantonal importData
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD/sz/oereb_kbs importData
```

```
./start-gretl.sh --docker-image sogis/gretl:latest --docker-network oereb_stack_default --job-directory $PWD :oereb_av:replaceCadastralSurveyingData :oereb_plzo:importPLZO :ch:oereb_bundesgesetze:importData :ch:oereb_bundeskonfiguration:importBundeskonfiguration :sh:oereb_kantonskonfiguration:importKantonskonfiguration :so:oereb_kantonskonfiguration:importKantonskonfiguration :sz:oereb_kantonskonfiguration:importKantonskonfiguration :ch:oereb_bundesdaten:importData :sh:oereb_kbs:importData :so:oereb_kbs:importData :so:oereb_grundwasserschutz:importData :so:oereb_nutzungsplanung:importData :so:oereb_nutzungsplanung_kantonal:importData :sz:oereb_kbs:importData
```

## Beispiele
SO:
- http://localhost:8080/extract/xml?EGRID=CH955832730623
- http://localhost:8080/extract/xml?EGRID=CH955832730623

SH:
- http://localhost:8080/extract/xml?EGRID=CH167308546127
- http://localhost:8080/extract/pdf?EGRID=CH167308546127

SZ:
- http://localhost:8080/extract/xml?EGRID=CH667722407539
- http://localhost:8080/extract/pdf?EGRID=CH667722407539

## Todo

- MapLayering: geodienste.ch Darstellungsdienste dürfen nur einmal vorkommen? -> Query in Code anschauen
- Bug wegen ili2pg-Update. Siehe ....