# To find Standard Deviation

## query for standard deviation

SELECT 
	neighborhood,
	MAX(price) AS max_price,
	MIN(price) AS min_price,
	MAX(price) - MIN(price) AS price_range,
	CAST(ROUND(AVG(price),-3) as int) AS mean_price,
	ROUND(STDDEV_SAMP(price), -3) AS standard_deviation
FROM 
	home_sales
GROUP BY 
	neighborhood;

## data preparation to see the above query in action

### database setup

CREATE TABLE home_sales (
	house_id INT PRIMARY KEY,
	neighborhood VARCHAR(50),
	price INT
);

INSERT INTO home_sales (house_id, neighborhood, price) VALUES
(101, 'Greenwood Heights', 450300),
(102, 'Greenwood Heights', 471200),
(103, 'Greenwood Heights', 433100),
(104, 'Greenwood Heights', 462000),
(105, 'Greenwood Heights', 445700),
(106, 'Greenwood Heights', 468900),
(107, 'Greenwood Heights', 453400),
(108, 'Greenwood Heights', 477100),
(109, 'Greenwood Heights', 440800),
(110, 'Greenwood Heights', 456600),
(111, 'Sunnyvale Meadows', 550500),
(112, 'Sunnyvale Meadows', 559200),
(113, 'Sunnyvale Meadows', 545800),
(114, 'Sunnyvale Meadows', 561400),
(115, 'Sunnyvale Meadows', 553600),
(116, 'Sunnyvale Meadows', 548700),
(117, 'Sunnyvale Meadows', 555500),
(118, 'Sunnyvale Meadows', 563800),
(119, 'Sunnyvale Meadows', 552400),
(120, 'Sunnyvale Meadows', 560200),
(121, 'Maplewood Estates', 350100),
(122, 'Maplewood Estates', 361200),
(123, 'Maplewood Estates', 342300),
(124, 'Maplewood Estates', 355600),
(125, 'Maplewood Estates', 348700),
(126, 'Maplewood Estates', 359800),
(127, 'Maplewood Estates', 353200),
(128, 'Maplewood Estates', 347900),
(129, 'Maplewood Estates', 344500),
(130, 'Maplewood Estates', 358300),
(131, 'Pinecrest Villas', 620400),
(132, 'Pinecrest Villas', 629300),
(133, 'Pinecrest Villas', 612800),
(134, 'Pinecrest Villas', 621600),
(135, 'Pinecrest Villas', 634500),
(136, 'Pinecrest Villas', 618900),
(137, 'Pinecrest Villas', 625400),
(138, 'Pinecrest Villas', 613100),
(139, 'Pinecrest Villas', 626700),
(140, 'Pinecrest Villas', 619200),
(141, 'Riverside Gardens', 480700),
(142, 'Riverside Gardens', 492300),
(143, 'Riverside Gardens', 471200),
(144, 'Riverside Gardens', 489400),
(145, 'Riverside Gardens', 475100),
(146, 'Riverside Gardens', 483600),
(147, 'Riverside Gardens', 478200),
(148, 'Riverside Gardens', 490500),
(149, 'Riverside Gardens', 473400),
(150, 'Riverside Gardens', 486700),
(151, 'Pinecrest Villas', 1120900), -- High outlier
(152, 'Pinecrest Villas', 315500), -- Low outlier;
(153, 'Pinecrest Villas', 619800),
(154, 'Pinecrest Villas', 620200),
(155, 'Pinecrest Villas', 620100),
(156, 'Pinecrest Villas', 620300),
(157, 'Pinecrest Villas', 619900),
(158, 'Pinecrest Villas', 620400),
(159, 'Pinecrest Villas', 620000),
(160, 'Pinecrest Villas', 620500),
(161, 'Pinecrest Villas', 620100),
(162, 'Pinecrest Villas', 619700),
(163, 'Pinecrest Villas', 619800),
(164, 'Pinecrest Villas', 620200),
(165, 'Pinecrest Villas', 620100),
(166, 'Pinecrest Villas', 620300),
(167, 'Pinecrest Villas', 619900),
(168, 'Pinecrest Villas', 620400),
(169, 'Pinecrest Villas', 620000),
(170, 'Pinecrest Villas', 620500),
(171, 'Pinecrest Villas', 620100),
(172, 'Pinecrest Villas', 619700);

SELECT 
	house_id,
	neighborhood,
	price
FROM home_sales;

## Mark your feedback at the Following Contact Points
- **LinkedIn:** <https://www.linkedin.com/in/rishirajopenminds>
- **GitHub:** <https://github.com/rishiraj88>

## Credits and Gratitude
- Thank all who have mentored, taught and guided. Also, always appreciate who have supported with pair programming and more.