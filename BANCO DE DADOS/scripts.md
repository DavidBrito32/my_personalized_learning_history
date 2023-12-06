--https://dontpad.com/fs17--
CREATE DATABASE IF NOT EXISTS digital_store;

	USE digital_store;

CREATE TABLE IF NOT EXISTS banners(
    banner_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    banner_image VARCHAR(100) NULL,
    banner_image_bg VARCHAR(100) NULL,
    banner_title VARCHAR(50) NOT NULL,
    banner_title_sup VARCHAR(50) NOT NULL,
    banner_discription VARCHAR(255) NOT NULL,
    banner_cta_text VARCHAR(20) NOT NULL,
    banner_status INTEGER DEFAULT 1
);

CREATE TABLE IF NOT EXISTS brands(
    brand_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    brand_name VARCHAR(20) NOT NULL,
    brand_status INTEGER DEFAULT 1 
);

INSERT INTO brands (brand_name) VALUES 
('Nike'),
('Adidas'),
('Olimpikus'),
('Puma'),
('Mizuno'),
('Penalty'),
('Okley'),
('Umbro'),
('New balance'),
('Lacoste');

SELECT * FROM brands;
SELECT brand_name FROM brands;
SELECT brand_name, brand_status FROM brands;
SELECT * FROM brands WHERE brand_name = 'nike';
SELECT * FROM brands WHERE brand_id = 1 AND brand_id = 2;

CREATE TABLE IF NOT EXISTS categories(
    category_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY, 
    category_name VARCHAR(20) NOT NULL,
    category_status INTEGER DEFAULT 1
);

INSERT INTO categories (category_name, category_status)
VALUES
('Tênis', 1),
('Camisetas', 1),
('Calças', 1),
('Bonés', 1),
('Headphones', 1),
('Bolsas', 0);

CREATE TABLE IF NOT EXISTS users(
    user_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY, 
    user_name VARCHAR(20) NOT NULL,
    user_status INTEGER DEFAULT 1,
    user_email VARCHAR(255) NOT NULL
);

ALTER TABLE users ADD (
    user_fone INTEGER NOT NULL,
    user_data_nasc DATE NOT NULL
);

CREATE TABLE IF NOT EXISTS reviews(
    review_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY, 
    review_rate INTEGER NOT NULL,
    user_id INTEGER NOT NULL,
    review_text VARCHAR(255) NULL,
    review_status INTEGER DEFAULT 1,
    FOREIGN KEY (user_id) REFERENCES users (user_id)
);

INSERT INTO reviews (review_rate, user_id, product_id)
SELECT 
    FLOOR(RAND() * 5) + 1 as review_rate, 
    1, 
    CASE 
        WHEN RAND() < 0.5 THEN 30
        ELSE 31 
    END as product_id
FROM 
    information_schema.tables
LIMIT 10;

CREATE TABLE IF NOT EXISTS genders(
	gender_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
	gender_name VARCHAR(50) NOT NULL,
	gender_status INTEGER DEFAULT 1
);

CREATE TABLE IF NOT EXISTS products(
    product_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    product_image BLOB(100) NULL,
    product_discount INTEGER NOT NULL,
    product_price FLOAT NOT NULL,
    product_sizes VARCHAR(50) NULL,
    product_name VARCHAR(20) NOT NULL,
    product_discription VARCHAR(255) NULL,
    product_category VARCHAR(10) NOT NULL,
    product_colors VARCHAR(10) NOT NULL,
    product_status INTEGER DEFAULT 1,
    product_condition INTEGER DEFAULT 1
);

ALTER TABLE products ADD(
    brand_id INTEGER FOREIGN KEY (brand_id) REFERENCES brands(brand_id),
    category_id INTEGER FOREIGN KEY (category_id) REFERENCES categories(category_id)
);

ALTER TABLE products DROP product_discription;
ALTER TABLE products ADD product_description VARCHAR(255) NULL;

INSERT INTO products (product_price, product_name, product_description, category_id, brand_id)
SELECT 
    ROUND(RAND() * (100 - 10) + 10, 2) as product_price, -- Valor decimal entre 10 e 100
    CASE 
        WHEN RAND() < 0.5 THEN 'Tênis' -- Metade das vezes será 'Tênis'
        ELSE 'Camisa' -- Metade das vezes será 'Camisa'
    END as product_name,
    SUBSTRING('Lorem ipsum dolor sit amet, consectetur adipiscing elit.', 1, FLOOR(RAND() * 50) + 1) as product_description, -- Lorem ipsum com até 50 caracteres
    FLOOR(RAND() * 5) + 1 as category_id, -- Número aleatório entre 1 e 5
    FLOOR(RAND() * 10) + 1 as brand_id -- Número aleatório entre 1 e 10
FROM 
    information_schema.tables
LIMIT 100; 

SELECT product_id, product_name, product_price, category_id, brand_id FROM products;
SELECT product_id, product_name, product_price, category_id, brand_id FROM products ORDER BY product_price ASC;

SELECT product_id, product_name, product_price, category_id, brand_id FROM products WHERE product_name LIKE '%camisa%';

SELECT product_id, product_name, product_price, brand_id, products.category_id, category_name, category_status FROM products INNER JOIN categories ON products.category_id = categories.category_id WHERE category_status = 1;

SELECT products.product_id, product_name, product_description, product_sizes, product_colors, product_price,  products.category_id, category_name, products.brand_id, brand_name 
FROM products 
INNER JOIN categories ON products.category_id = categories.category_id 
INNER JOIN brands ON products.brand_id = brands.brand_id
WHERE products.product_id = 30;

SELECT product_id, product_image_url FROM products_images WHERE product_id = 30;
SELECT COUNT(*) FROM reviews WHERE product_id = 30;
SELECT AVG(review_rate) AS rate_medium FROM reviews WHERE product_id = 30;
SELECT product_name, brand_id, category_id FROM products WHERE brand_id = 1 AND category_id = 5 LIMIT 4;



SELECT product_id, product_name, product_price, category_id, brand_id FROM products WHERE product_price > 15 AND product_price < 30 ORDER BY product_price;

SELECT COUNT(*) FROM products WHERE product_price < 30;

UPDATE products SET product_name = 'camisa 1' WHERE product_id = 4;

CREATE TABLE IF NOT EXISTS products_images (
	product_image_id INTEGER AUTO_INCREMENT PRIMARY KEY,
	product_image_url VARCHAR(100) NOT NULL,
	product_id INTEGER NOT NULL,
	FOREIGN KEY(product_id) REFERENCES products (product_id)
);

INSERT INTO products_images (product_image_url, product_id)
VALUES
('https://imgnike-a.akamaihd.net/768x768/027796NX.jpg', 30),
('https://imgnike-a.akamaihd.net/768x768/027796NXA1.jpg', 30),
('https://imgnike-a.akamaihd.net/768x768/027796NXA2.jpg', 30),
('https://imgnike-a.akamaihd.net/768x768/027796NXA3.jpg', 31);

CREATE TABLE IF NOT EXISTS collections(
    collection_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    collection_image_bg BLOB(100) NULL,
    collection_discount INTEGER NOT NULL,
    collection_title VARCHAR(10) NOT NULL,
    collection_cta_txt VARCHAR(250) NOT NULL,
    collection_status INTEGER DEFAULT 1
);

CREATE TABLE IF NOT EXISTS orders(
    order_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    total_order INTEGER NOT NULL,
    total_order_discount INTEGER NOT NULL,
    order_ship VARCHAR(10) NOT NULL,
    order_status INTEGER DEFAULT 1,
    user_id INTEGER,
    FOREIGN KEY(user_id) REFERENCES users (user_id)
);

CREATE TABLE IF NOT EXISTS carts(
    cart_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    cart_products VARCHAR(100) NOT NULL
);