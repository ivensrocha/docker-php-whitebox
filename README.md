Clean installation for PHP, Apache and Magento requirements

docker run --name abib2bconvergence_whitebox -d -v <path>:/var/www/html ivens/php-whitebox

# composer init

{
    "name": "root/testcode",
    "authors": [
        {
            "name": "Ivens",
            "email": "ivens@ivens.pro"
        }
    ],
    "repositories": [
        {
            "type": "composer",
            "url": "https://repo.magento.com/"
        },
        {
            "type": "composer",
            "url": "http://webjumpdev.com/"
        }
    ],
    "require": {
        "webjump/library-abib2b-http-client-service": "dev-develop",
        "webjump/library-abib2b-product-abi-service": "dev-develop"
    },
    "autoload": {
        "psr-4": {
            "Webjump\\Test\\Integration\\": "code/"
        }
    },
    "config": {
        "secure-http": false
    }
}



mkdir -p ~/.composer && echo '{"github-oauth":{"github.com":"'$GITHUB_TOKEN'"},"http-basic":{"repo.magento.com":{"username":"'$REPO_MAGENTO_USERNAME'","password":"'$REPO_MAGENTO_PASSWORD'"}}}' > ~/.composer/auth.json

ln -s /var/www/html/src/lib/internal/Webjump/ProductABIService/ library-abib2b-product-abi-service
