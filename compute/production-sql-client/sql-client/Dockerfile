###############################################################################
#  Licensed to the Apache Software Foundation (ASF) under one
#  or more contributor license agreements.  See the NOTICE file
#  distributed with this work for additional information
#  regarding copyright ownership.  The ASF licenses this file
#  to you under the Apache License, Version 2.0 (the
#  "License"); you may not use this file except in compliance
#  with the License.  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
# limitations under the License.
###############################################################################


###############################################################################
#SQL CLI - inspired by https://github.com/wuchong/flink-sql-demo/tree/v1.11-EN/sql-client
#SQL CLI - inspired by https://github.com/Aiven-Open/sql-cli-for-apache-flink-docker.git
###############################################################################

FROM flink:1.20

# Create CLI lib folder
COPY sql-client/bin/* /opt/sql-client/
RUN mkdir -p /opt/sql-client/lib

# Download connector libraries
RUN wget -P /opt/sql-client/lib/ https://repo1.maven.org/maven2/org/apache/paimon/paimon-flink-1.20/1.1.1/paimon-flink-1.20-1.1.1.jar; \
    wget -P /opt/sql-client/lib/ https://repo1.maven.org/maven2/org/apache/flink/flink-shaded-hadoop-2/2.8.3-10.0/flink-shaded-hadoop-2-2.8.3-10.0.jar;

# Copy configuration
COPY sql-client/conf/* /opt/flink/conf/

WORKDIR /opt/sql-client
ENV SQL_CLIENT_HOME /opt/sql-client

COPY sql-client/docker-entrypoint.sh /

RUN chmod 777 /docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]