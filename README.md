codebrag-modified
===============

To start:
-----
```bash
docker run --name codebrag -d --restart=always -p 80:8080 -v PATH_TO_REPOSITORIES:/repos -v PATH_TO_H2_FOLDER:/opt/codebrag/data acdcjunior/codebrag-modified
```

To edit the database:
-----

To edit the database, **STOP the `codebrag` container**, and:

```bash
docker run --name codebrag-h2 -it --entrypoint=/bin/bash -p 82:8082 -v PATH_TO_H2_FOLDER:/opt/codebrag/data acdcjunior/codebrag-modified -i

# And, inside the container (while at /opt/codebrag/):
java -cp codebrag-dist-assembly-2.3.4.jar org.h2.tools.Server -webAllowOthers -ifExists -baseDir /opt/codebrag/data
```
Now open your browser at `http://name-of-the-server-where-you-started-the-docker:82`

Use as URL: `jdbc:h2:/opt/codebrag/data`
Keep user and password blank.
