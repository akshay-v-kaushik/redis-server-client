FROM gcc:latest
WORKDIR /app
COPY . .
RUN g++ -Wall -Wextra -O2 -g 14_server.cpp avl.cpp hashtable.cpp heap.cpp thread_pool.cpp zset.cpp -o server
EXPOSE 1234
RUN ls -l /app
CMD ["/app/server"]
