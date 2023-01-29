[Example dataset](https://clickhouse.com/docs/ru/getting-started/example-datasets/cell-towers)

Работа с ClickHouse

# Install
1. Установить зависимости composer
    ```
    docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php82-composer:latest \
    composer install --ignore-platform-reqs
    ```
2. Скачать dataset и переместить его в clickhouse/cell_towers.csv
3. Раскоменитруйте в docker-compose.yml 
    ```
    './clickhouse/init-db.sh:/docker-entrypoint-initdb. d/init-db.sh'
    ```
4. Запустить проект
    ```
    ./vendor/bin/sail up -d
    ```
5. Закоментируйте в docker-compose.yml 
    ```
    './clickhouse/init-db.sh:/docker-entrypoint-initdb. d/init-db.sh'
    ```
6. Установить зависимости npm
    ```
    ./vendor/bin/sail npm i
    ```
7. Заупстить Vite
    ```
    ./vendor/bin/sail npm run dev
    ```