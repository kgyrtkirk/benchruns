prepare:
```
#!/bin/bash
set -e
git checkout "$1"
git clean -dfx
mvn install -pl benchmarks/ -am -DskipTests -Pskip-static-checks
cp benchmarks/target/benchmarks.jar ~/bench/${1}.jar
```


run:
```

mkdir run2
for f in *.jar;do java -jar $f -rf json -rff run2/out.$f.json ExpressionSelectorBenchmark;done

```

https://jmh.morethan.io/?sources=https://raw.githubusercontent.com/kgyrtkirk/benchruns/main/pr-16800/out.pr-16800.jar.json,https://raw.githubusercontent.com/kgyrtkirk/benchruns/main/pr-16800/out.base.jar.json

https://jmh.morethan.io/?sources=https://raw.githubusercontent.com/kgyrtkirk/benchruns/main/pr-16800/out.pr-16800.jar.json,https://raw.githubusercontent.com/kgyrtkirk/benchruns/main/pr-16800/out.base.jar.json
