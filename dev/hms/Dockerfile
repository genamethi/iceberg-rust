# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM apache/hive:4.2.1

USER root

# Link the hadoop-aws and AWS SDK jars that the image ships into the metastore classpath
ADD --chmod=644 --checksum=sha256:a18508b9348af095ea41301e439354dbd449e304ac44c6885b2b4fe78de88126 \
  https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/${HADOOP_VERSION}/hadoop-aws-${HADOOP_VERSION}.jar \
  /opt/hive/lib/hadoop-aws-${HADOOP_VERSION}.jar
ADD --chmod=644 --checksum=sha256:faf78ac4880f56cf52791d84ec1068ce7c66acc4295d580a726104b734c01fcd \
  https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk-bundle/1.11.271/aws-java-sdk-bundle-1.11.271.jar \
  /opt/hive/lib/aws-java-sdk-bundle-1.11.271.jar

# The entrypoint links this directory into the Hive config directory, over its own core-site.xml
ENV HIVE_CUSTOM_CONF_DIR=/opt/hive/custom-conf
COPY core-site.xml ${HIVE_CUSTOM_CONF_DIR}/core-site.xml

USER hive
