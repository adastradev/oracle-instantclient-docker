FROM oraclelinux:7-slim

ENV PATH $PATH:/usr/lib/oracle/18.3/client64/bin

RUN curl -o /etc/yum.repos.d/public-yum-ol7.repo https://yum.oracle.com/public-yum-ol7.repo 2>/dev/null &&\
    yum-config-manager --enable ol7_oracle_instantclient &&\
    yum -y install oracle-instantclient18.3-basiclite &&\
    rm -rf /var/cache/yum &&\
    echo /usr/lib/oracle/18.3/client64/lib > /etc/ld.so.conf.d/oracle-instantclient18.3.conf &&\
    ldconfig

# Oracle config files
ENV TNS_ADMIN /admin
VOLUME /admin
