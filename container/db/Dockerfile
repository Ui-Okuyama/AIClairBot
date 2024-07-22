FROM postgres:16.3

WORKDIR /tmp
RUN git clone --branch v0.7.2 https://github.com/pgvector/pgvector.git
WORKDIR pgvector
RUN make
RUN make install