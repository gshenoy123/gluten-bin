# Intel OAP Gluten binary
- [x] Gluten JAR binaries and commands <br>


## commands

* ./spark-submit.sh --master spark://DESKTOP-3BFS87C.:7077 --driver-memory=1g --executor-memory=1g --driver-cores=1 --executor-cores=1 --class org.amma.samples.sparksubmit.SparkMain "/mnt/d/dev/projects/spark-submit-example/target/neo-calc.jar"

* ./spark-submit.sh --master spark://DESKTOP-3BFS87C.:7077 \
  --conf spark.plugins=io.glutenproject.GlutenPlugin \
  --conf spark.gluten.sql.columnar.backend.lib=velox \
  --conf spark.driver.extraClassPath="/mnt/d/dev/projects/gluten/backends-velox/target/gluten-velox-bundle-spark3.3_2.12-ubuntu_22.04-0.5.0-SNAPSHOT.jar:/mnt/d/dev/projects/gluten/backends-velox/target/backends-velox-0.5.0-SNAPSHOT-3.3.jar" \
  --conf spark.executor.extraClassPath="/mnt/d/dev/projects/gluten/backends-velox/target/gluten-velox-bundle-spark3.3_2.12-ubuntu_22.04-0.5.0-SNAPSHOT.jar:/mnt/d/dev/projects/gluten/backends-velox/target/backends-velox-0.5.0-SNAPSHOT-3.3.jar" \
  --conf spark.memory.offHeap.enabled=true \
  --conf spark.memory.offHeap.size=512m \
  --conf spark.gluten.sql.columnar.forceshuffledhashjoin=true \
  --conf spark.shuffle.manager=org.apache.spark.shuffle.sort.ColumnarShuffleManager \
  --conf spark.gluten.sql.columnar.iterator=true \
  --conf spark.gluten.sql.columnar.loadarrow=false \
  --conf spark.gluten.sql.columnar.backend.lib=velox \
  --num-executors 1 \
  --executor-cores 1 \
  --driver-memory 1g \
  --executor-memory 2g \
  --conf spark.executor.memoryOverhead=1g \
  --conf spark.driver.maxResultSize=256m \
  --class org.amma.samples.sparksubmit.SparkMain "/mnt/d/dev/projects/spark-submit-example/target/neo-calc.jar"