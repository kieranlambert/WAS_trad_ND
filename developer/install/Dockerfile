############################################################################
# (C) Copyright IBM Corporation 2015, 2016                                 #
#                                                                          #
# Licensed under the Apache License, Version 2.0 (the "License");          #
# you may not use this file except in compliance with the License.         #
# You may obtain a copy of the License at                                  #
#                                                                          #
#      http://www.apache.org/licenses/LICENSE-2.0                          #
#                                                                          #
# Unless required by applicable law or agreed to in writing, software      #
# distributed under the License is distributed on an "AS IS" BASIS,        #
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. #
# See the License for the specific language governing permissions and      #
# limitations under the License.                                           #
#                                                                          #
############################################################################

FROM ubuntu:16.04

MAINTAINER David Currie <david_currie@uk.ibm.com>

RUN apt-get update && apt-get install -y openssl

ADD was.tar /
COPY createProfileAndStartServer.sh modifyPassword.sh updateHostName.py updatePassword.py /work/

ARG USER=was
ARG GROUP=was

RUN groupadd $GROUP \
  && useradd $USER -g $GROUP -m \
  && chown -R $USER:$GROUP /work /opt \
  && chmod +x /work/*sh 

USER $USER

ENV PATH /opt/IBM/WebSphere/AppServer/bin:$PATH

CMD ["/work/createProfileAndStartServer.sh"]
