-- phpMyAdmin SQL Dump
-- version 5.2.1
-- https://www.phpmyadmin.net/
--
-- Host: localhost:3306
-- Generation Time: Mar 17, 2024 at 04:57 AM
-- Server version: 10.6.15-MariaDB
-- PHP Version: 8.1.16

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `memmisg_avator`
--

-- --------------------------------------------------------

--
-- Table structure for table `admins`
--

CREATE TABLE `admins` (
  `admin_id` int(11) NOT NULL,
  `username` varchar(225) DEFAULT NULL,
  `password` text NOT NULL,
  `register_date` datetime NOT NULL,
  `login_date` datetime DEFAULT NULL,
  `login_ip` varchar(225) DEFAULT NULL,
  `client_type` enum('1','2') NOT NULL DEFAULT '2' COMMENT '2 -> ON, 1 -> OFF',
  `access` varchar(999) NOT NULL,
  `mode` varchar(225) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `admins`
--

INSERT INTO `admins` (`admin_id`, `username`, `password`, `register_date`, `login_date`, `login_ip`, `client_type`, `access`, `mode`) VALUES
(1, 'admin', 'admin', '2021-09-08 10:19:05', '2024-03-17 10:04:52', '103.69.94.36', '2', '{\"admin_access\":\"1\",\"users\":\"1\",\"orders\":\"1\",\"subscriptions\":\"1\",\"dripfeed\":\"1\",\"services\":\"1\",\"payments\":\"1\",\"tickets\":\"1\",\"reports\":\"1\",\"general_settings\":\"1\",\"pages\":\"1\",\"payments_settings\":\"1\",\"bank_accounts\":\"1\",\"payments_bonus\":\"1\",\"alert_settings\":\"1\",\"providers\":\"1\",\"themes\":\"1\",\"child-panels\":\"1\",\"language\":\"1\",\"meta\":\"1\",\"twice\":\"1\",\"files\":\"1\",\"coupon\":\"1\",\"admins\":\"1\",\"update-prices\":\"1\",\"bulk\":\"1\",\"bulkc\":\"1\",\"synced-logs\":\"1\",\"refill\":\"1\",\"referral\":\"1\",\"broadcast\":\"1\",\"logs\":\"1\",\"videop\":\"1\",\"updates\":\"1\",\"menu\":\"1\",\"inte\":\"1\",\"currency\":\"1\",\"news\":\"1\",\"blog\":\"1\",\"modules\":\"1\",\"subject\":\"1\"}', 'sun');

-- --------------------------------------------------------

--
-- Table structure for table `article`
--

CREATE TABLE `article` (
  `id` int(11) NOT NULL,
  `title` varchar(128) NOT NULL,
  `content` text NOT NULL,
  `published_at` datetime DEFAULT NULL,
  `image_file` varchar(200) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- --------------------------------------------------------

--
-- Table structure for table `bank_accounts`
--

CREATE TABLE `bank_accounts` (
  `id` int(11) NOT NULL,
  `bank_name` varchar(225) NOT NULL,
  `bank_sube` varchar(225) NOT NULL,
  `bank_hesap` varchar(225) NOT NULL,
  `bank_iban` text NOT NULL,
  `bank_alici` varchar(225) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `bank_accounts`
--

INSERT INTO `bank_accounts` (`id`, `bank_name`, `bank_sube`, `bank_hesap`, `bank_iban`, `bank_alici`) VALUES
(1, 'VodaFone-Cash', '+201019645374', '+201019645374', '+201019645374', 'Mohamed Yasser');

-- --------------------------------------------------------

--
-- Table structure for table `blogs`
--

CREATE TABLE `blogs` (
  `id` int(11) NOT NULL,
  `title` varchar(128) NOT NULL,
  `content` text NOT NULL,
  `published_at` datetime NOT NULL,
  `image_file` varchar(200) DEFAULT NULL,
  `status` enum('1','2') NOT NULL DEFAULT '1',
  `blog_get` varchar(225) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `updated_at` datetime NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

--
-- Dumping data for table `blogs`
--

INSERT INTO `blogs` (`id`, `title`, `content`, `published_at`, `image_file`, `status`, `blog_get`, `updated_at`) VALUES
(1, 'Welcome', 'Testing Blog\r\n\r\n\r\n\r\n\r\n\r\nYou can add posts here', '2022-12-27 01:17:16', 'https://te.legra.ph/file/0cc299407f858f7a89662.jpg', '1', 'test', '0000-00-00 00:00:00');

-- --------------------------------------------------------

--
-- Table structure for table `bulkedit`
--

CREATE TABLE `bulkedit` (
  `id` int(11) NOT NULL,
  `service_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `categories`
--

CREATE TABLE `categories` (
  `category_id` int(11) NOT NULL,
  `category_name` text NOT NULL,
  `category_line` double NOT NULL,
  `category_type` enum('1','2') CHARACTER SET utf8mb3 COLLATE utf8mb3_general_ci NOT NULL DEFAULT '2',
  `category_secret` enum('1','2') NOT NULL DEFAULT '2',
  `category_icon` text NOT NULL,
  `is_refill` enum('1','2') CHARACTER SET utf8mb3 COLLATE utf8mb3_general_ci NOT NULL DEFAULT '1'
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_bin;

-- --------------------------------------------------------

--
-- Table structure for table `childpanels`
--

CREATE TABLE `childpanels` (
  `id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `domain` varchar(191) NOT NULL,
  `currency` varchar(191) NOT NULL,
  `child_username` varchar(191) NOT NULL,
  `child_password` varchar(191) NOT NULL,
  `charge` double NOT NULL,
  `status` enum('Pending','Active','Frozen','Suspended') NOT NULL DEFAULT 'Pending',
  `renewal_date` date NOT NULL,
  `date_created` datetime NOT NULL,
  `dreampanel_id` int(11) NOT NULL,
  `keyc` varchar(225) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_unicode_ci;

--
-- Dumping data for table `childpanels`
--

INSERT INTO `childpanels` (`id`, `client_id`, `domain`, `currency`, `child_username`, `child_password`, `charge`, `status`, `renewal_date`, `date_created`, `dreampanel_id`, `keyc`) VALUES
(1, 2, 'asdasdasd.com', 'USD', 'qweqwe123', 'qweqwe123', 1, 'Pending', '2022-05-27', '2022-04-27 19:56:50', 0, 'b1fbedd6f1266a8990bf648919068680'),
(2, 1, 'dasdasd', 'USD', 'abdosapry114', 'qweqwe123', 1, 'Pending', '2022-05-29', '2022-04-29 00:04:15', 0, 'b1fbedd6f1266a8990bf648919068680'),
(3, 1, 'asdasdasdsd', 'USD', 'abdosapry114', 'qweqwe123', 1, 'Pending', '2022-05-29', '2022-04-29 00:05:26', 0, 'b1fbedd6f1266a8990bf648919068680'),
(4, 1, 'sfsdfsdfsd', 'USD', 'erer', 'qweqwe123', 1, 'Pending', '2022-06-06', '2022-05-06 20:39:16', 0, 'b1fbedd6f1266a8990bf648919068680');

-- --------------------------------------------------------

--
-- Table structure for table `clients`
--

CREATE TABLE `clients` (
  `client_id` int(11) NOT NULL,
  `name` varchar(225) DEFAULT NULL,
  `email` varchar(225) NOT NULL,
  `username` varchar(225) DEFAULT NULL,
  `admin_type` enum('1','2') NOT NULL DEFAULT '2',
  `password` text NOT NULL,
  `telephone` varchar(225) DEFAULT NULL,
  `balance` decimal(21,4) NOT NULL,
  `balance_type` enum('1','2') NOT NULL DEFAULT '2',
  `debit_limit` double DEFAULT NULL,
  `spent` decimal(21,4) NOT NULL,
  `register_date` datetime NOT NULL,
  `login_date` datetime DEFAULT NULL,
  `login_ip` varchar(225) DEFAULT NULL,
  `apikey` text NOT NULL,
  `tel_type` enum('1','2') NOT NULL DEFAULT '1' COMMENT '2 -> ON, 1 -> OFF',
  `email_type` enum('1','2') NOT NULL DEFAULT '1' COMMENT '2 -> ON, 1 -> OFF',
  `client_type` enum('1','2') NOT NULL DEFAULT '2' COMMENT '2 -> ON, 1 -> OFF',
  `access` text DEFAULT NULL,
  `lang` varchar(255) NOT NULL DEFAULT 'tr',
  `timezone` double NOT NULL DEFAULT 0,
  `currency_type` enum('INR','USD') NOT NULL DEFAULT 'USD',
  `ref_code` text NOT NULL,
  `ref_by` text DEFAULT NULL,
  `change_email` enum('1','2') NOT NULL DEFAULT '2',
  `resend_max` int(11) NOT NULL,
  `currency` varchar(225) NOT NULL DEFAULT '1',
  `passwordreset_token` varchar(225) NOT NULL,
  `coustm_rate` int(11) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `clients_category`
--

CREATE TABLE `clients_category` (
  `id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `category_id` int(11) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `clients_price`
--

CREATE TABLE `clients_price` (
  `id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `service_id` int(11) NOT NULL,
  `service_price` double NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `clients_service`
--

CREATE TABLE `clients_service` (
  `id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `service_id` int(11) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `client_report`
--

CREATE TABLE `client_report` (
  `id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `action` text NOT NULL,
  `report_ip` varchar(225) NOT NULL,
  `report_date` datetime NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `client_report`
--

INSERT INTO `client_report` (`id`, `client_id`, `action`, `report_ip`, `report_date`) VALUES
(1, 1, '\r\n    User registered.', '102.191.182.97', '2022-04-23 21:03:27'),
(2, 2, '\r\n    User registered.', '102.191.182.97', '2022-04-23 21:09:14'),
(3, 2, 'API Key changed', '102.191.182.97', '2022-04-23 21:38:02'),
(4, 2, '0 New Order #1.', '102.191.182.97', '2022-04-23 21:39:08'),
(5, 2, '0 New Order #2.', '102.191.182.97', '2022-04-23 21:39:25'),
(6, 2, 'Member logged in.', '102.191.182.97', '2022-04-23 22:56:57'),
(7, 2, 'Member logged in.', '102.191.182.97', '2022-04-23 22:57:09'),
(8, 1, 'Member logged in.', '156.220.137.147', '2022-04-24 11:35:10'),
(9, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 15:57:27'),
(10, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 16:58:35'),
(11, 2, 'Member logged in.', '102.191.182.97', '2022-04-24 17:01:49'),
(12, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 17:40:45'),
(13, 1, 'API Key changed', '102.191.182.97', '2022-04-24 17:55:04'),
(14, 1, 'API Key changed', '102.191.182.97', '2022-04-24 17:56:14'),
(15, 1, 'API Key changed', '102.191.182.97', '2022-04-24 17:56:31'),
(16, 1, 'API Key changed', '102.191.182.97', '2022-04-24 17:56:37'),
(17, 1, 'API Key changed', '102.191.182.97', '2022-04-24 18:00:16'),
(18, 1, 'API Key changed', '102.191.182.97', '2022-04-24 18:00:45'),
(19, 1, 'New support ticket created#1', '102.191.182.97', '2022-04-24 18:26:55'),
(20, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 18:38:59'),
(21, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 19:13:00'),
(22, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 19:13:52'),
(23, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 19:15:36'),
(24, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 19:36:11'),
(25, 3, '\r\n    User registered.', '102.186.161.181', '2022-04-24 19:56:12'),
(26, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 20:00:03'),
(27, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 20:00:55'),
(28, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 20:26:06'),
(29, 1, 'Support request answered#1', '102.191.182.97', '2022-04-24 20:29:29'),
(30, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 20:31:53'),
(31, 4, '\r\n    User registered.', '102.191.182.97', '2022-04-24 20:38:57'),
(32, 5, '\r\n    User registered.', '102.191.182.97', '2022-04-24 20:39:46'),
(33, 5, 'API Key changed', '102.191.182.97', '2022-04-24 21:21:54'),
(34, 1, 'Member logged in.', '102.191.182.97', '2022-04-24 21:53:52'),
(35, 5, 'Member logged in.', '102.191.182.97', '2022-04-24 22:21:03'),
(36, 6, '\r\n    User registered.', '102.191.182.97', '2022-04-24 22:33:41'),
(37, 3, 'Member logged in.', '102.186.161.181', '2022-04-24 23:16:29'),
(38, 1, 'Member logged in.', '102.191.182.97', '2022-04-25 12:24:25'),
(39, 7, '\r\n    User registered.', '196.135.101.128', '2022-04-25 12:26:06'),
(40, 1, 'Member logged in.', '102.191.182.97', '2022-04-25 13:53:02'),
(41, 1, 'Member logged in.', '102.191.182.97', '2022-04-25 15:53:45'),
(42, 1, 'Member logged in.', '102.191.182.97', '2022-04-25 16:21:18'),
(43, 1, 'Member logged in.', '102.191.182.97', '2022-04-25 16:39:04'),
(44, 1, 'Member logged in.', '102.191.182.97', '2022-04-25 18:32:14'),
(45, 1, '0.07 New Order #3.', '102.191.182.97', '2022-04-25 20:27:36'),
(46, 1, 'New support ticket created#2', '102.191.182.97', '2022-04-26 01:48:34'),
(47, 1, 'Support request answered#2', '102.191.182.97', '2022-04-26 03:30:50'),
(48, 1, 'Support request answered#2', '102.191.182.97', '2022-04-26 03:30:55'),
(49, 1, 'Support request answered#2', '102.191.182.97', '2022-04-26 03:31:32'),
(50, 1, 'Support request answered#2', '102.191.182.97', '2022-04-26 03:32:38'),
(51, 1, 'API Key changed', '102.191.182.97', '2022-04-26 04:02:26'),
(52, 1, 'API Key changed', '102.191.182.97', '2022-04-26 04:03:14'),
(53, 1, 'API Key changed', '102.191.182.97', '2022-04-26 04:03:51'),
(54, 8, '\r\n    User registered.', '102.191.182.97', '2022-04-26 04:44:20'),
(55, 8, 'API Key changed', '102.191.182.97', '2022-04-26 04:44:55'),
(56, 1, 'Member logged in.', '102.191.182.97', '2022-04-26 04:52:08'),
(57, 9, '\r\n    User registered.', '41.199.136.98', '2022-04-26 07:51:16'),
(58, 1, 'Member logged in.', '102.191.182.97', '2022-04-26 11:42:12'),
(59, 1, 'Member logged in.', '102.191.182.97', '2022-04-26 12:13:31'),
(60, 10, '\r\n    User registered.', '102.191.182.97', '2022-04-26 12:14:13'),
(61, 11, '\r\n    User registered.', '49.32.233.42', '2022-04-26 12:42:18'),
(62, 11, '0 New Order #4.', '49.32.233.42', '2022-04-26 12:46:07'),
(63, 1, 'Member logged in.', '102.191.182.97', '2022-04-26 13:02:20'),
(64, 12, '\r\n    User registered.', '102.191.182.97', '2022-04-26 13:21:13'),
(65, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:06:02'),
(66, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:06:33'),
(67, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:06:41'),
(68, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:06:47'),
(69, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:06:53'),
(70, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:01'),
(71, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:09'),
(72, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:18'),
(73, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:24'),
(74, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:31'),
(75, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:37'),
(76, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:44'),
(77, 12, 'API Key changed', '102.191.182.97', '2022-04-26 14:07:49'),
(78, 1, 'Member logged in.', '102.191.182.97', '2022-04-26 14:31:45'),
(79, 1, '0.07 New Order #5.', '102.191.182.97', '2022-04-26 14:32:57'),
(80, 1, 'Member logged in.', '102.191.182.97', '2022-04-26 14:43:09'),
(81, 1, 'Member logged in.', '156.220.30.83', '2022-04-26 14:48:48'),
(82, 1, 'New support ticket created#3', '156.220.30.83', '2022-04-26 14:49:38'),
(83, 1, 'Member logged in.', '156.220.30.83', '2022-04-26 14:50:49'),
(84, 1, 'Member logged in.', '102.191.182.97', '2022-04-26 18:29:17'),
(85, 13, '\r\n    User registered.', '136.158.28.35', '2022-04-27 00:26:38'),
(86, 13, '2.38 New Order #6.', '136.158.28.35', '2022-04-27 00:42:10'),
(87, 14, '\r\n    User registered.', '156.199.65.144', '2022-04-27 14:41:47'),
(88, 15, '\r\n    User registered.', '47.15.5.24', '2022-04-27 16:24:57'),
(89, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 17:50:17'),
(90, 1, 'New support ticket created#4', '102.191.182.97', '2022-04-27 17:50:25'),
(91, 1, 'Support request answered#4', '102.191.182.97', '2022-04-27 17:56:06'),
(92, 1, 'New support ticket created#5', '102.191.182.97', '2022-04-27 18:33:19'),
(93, 1, 'Support request answered#5', '102.191.182.97', '2022-04-27 18:35:38'),
(94, 16, '\r\n    User registered.', '102.191.182.97', '2022-04-27 18:37:22'),
(95, 17, '\r\n    User registered.', '102.191.182.97', '2022-04-27 18:44:34'),
(96, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 18:56:59'),
(97, 2, 'Member logged in.', '102.191.182.97', '2022-04-27 19:37:28'),
(98, 2, '0.1 New Order #7.', '102.191.182.97', '2022-04-27 19:38:10'),
(99, 2, '0.1 New Order #8.', '102.191.182.97', '2022-04-27 19:48:16'),
(100, 2, '0.1 New Order #9.', '102.191.182.97', '2022-04-27 19:50:13'),
(101, 2, 'New Child Panel Order with id : 1.', '102.191.182.97', '2022-04-27 19:56:50'),
(102, 2, 'Child Panel Renewed with id : 1.', '102.191.182.97', '2022-04-27 20:13:09'),
(103, 18, '\r\n    User registered.', '185.81.141.232', '2022-04-27 20:16:05'),
(104, 19, '\r\n    User registered.', '154.178.57.91', '2022-04-27 20:21:08'),
(105, 19, '9.92 New Order #10.', '185.81.141.232', '2022-04-27 20:31:05'),
(106, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 21:53:47'),
(107, 20, '\r\n    User registered.', '102.191.182.97', '2022-04-27 21:54:12'),
(108, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 21:54:29'),
(109, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 21:56:04'),
(110, 21, '\r\n    User registered.', '41.216.203.34', '2022-04-27 22:13:13'),
(111, 22, '\r\n    User registered.', '156.209.117.173', '2022-04-27 22:13:44'),
(112, 23, '\r\n    User registered.', '46.213.82.212', '2022-04-27 22:17:32'),
(113, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 22:23:06'),
(114, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 22:23:53'),
(115, 1, 'Member logged in.', '102.191.182.97', '2022-04-27 22:24:11'),
(116, 24, '\r\n    User registered.', '102.191.182.97', '2022-04-27 22:33:19'),
(117, 25, '\r\n    User registered.', '197.59.39.130', '2022-04-27 22:42:10'),
(118, 2, 'Member logged in.', '102.191.182.97', '2022-04-27 23:35:37'),
(119, 26, '\r\n    User registered.', '196.150.43.241', '2022-04-28 00:45:05'),
(120, 27, '\r\n    User registered.', '92.253.31.65', '2022-04-28 00:59:50'),
(121, 28, '\r\n    User registered.', '102.42.241.46', '2022-04-28 10:49:52'),
(122, 2, 'Member logged in.', '102.191.182.97', '2022-04-28 12:30:07'),
(123, 29, '\r\n    User registered.', '102.191.182.97', '2022-04-28 12:49:30'),
(124, 2, 'Member logged in.', '102.191.182.97', '2022-04-28 12:49:41'),
(125, 29, 'Member logged in.', '102.191.182.97', '2022-04-28 12:50:40'),
(126, 2, 'Member logged in.', '102.191.182.97', '2022-04-28 12:54:33'),
(127, 30, '\r\n    User registered.', '102.191.182.97', '2022-04-28 13:35:48'),
(128, 2, 'Member logged in.', '102.191.182.97', '2022-04-28 13:36:01'),
(129, 31, '\r\n    User registered.', '102.191.182.97', '2022-04-28 14:30:19'),
(130, 2, 'Member logged in.', '102.191.182.97', '2022-04-28 14:30:27'),
(131, 2, '0.1 New Order #11.', '102.191.182.97', '2022-04-28 14:44:50'),
(132, 2, 'New support ticket created#6', '102.191.182.97', '2022-04-28 14:47:13'),
(133, 2, 'Support request <strong>Automatic</strong> answered as. ID:6', '102.191.182.97', '2022-04-28 14:47:13'),
(134, 2, '0.001 New Order #12.', '102.191.182.97', '2022-04-28 14:59:20'),
(135, 2, '0.001 New Order #13.', '102.191.182.97', '2022-04-28 15:05:29'),
(136, 2, 'New support ticket created#7', '102.191.182.97', '2022-04-28 16:41:52'),
(137, 2, 'Support request answered#6', '102.191.182.97', '2022-04-28 16:45:04'),
(138, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 16:52:05'),
(139, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 16:57:48'),
(140, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 17:02:58'),
(141, 32, '\r\n    User registered.', '102.191.182.97', '2022-04-28 17:06:39'),
(142, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 17:14:30'),
(143, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 17:14:54'),
(144, 33, '\r\n    User registered.', '102.191.182.97', '2022-04-28 20:55:54'),
(145, 33, 'API Key changed', '102.191.182.97', '2022-04-28 20:59:13'),
(146, 34, '\r\n    User registered.', '102.191.182.97', '2022-04-28 21:00:25'),
(147, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 22:20:37'),
(148, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 22:22:51'),
(149, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 22:26:10'),
(150, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 22:28:40'),
(151, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 22:38:09'),
(152, 14, 'Member logged in.', '156.207.149.76', '2022-04-28 22:40:36'),
(153, 35, '\r\n    User registered.', '102.186.177.23', '2022-04-28 22:40:37'),
(154, 1, '0.07 New Order #14.', '102.191.182.97', '2022-04-28 23:28:29'),
(155, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 23:39:54'),
(156, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 23:51:13'),
(157, 1, 'Member logged in.', '102.191.182.97', '2022-04-28 23:55:46'),
(158, 1, 'New Child Panel Order with id : 2.', '102.191.182.97', '2022-04-29 00:04:15'),
(159, 1, 'New Child Panel Order with id : 3.', '102.191.182.97', '2022-04-29 00:05:26'),
(160, 2, 'Member logged in.', '105.196.120.167', '2022-05-05 20:26:18'),
(161, 1, 'Member logged in.', '105.196.120.167', '2022-05-05 22:22:08'),
(162, 1, 'Member logged in.', '102.191.102.29', '2022-05-06 01:44:31'),
(163, 1, 'Member logged in.', '102.191.102.29', '2022-05-06 03:43:26'),
(164, 1, 'Member logged in.', '102.191.102.29', '2022-05-06 03:48:14'),
(165, 1, '0.07 New Order #15.', '102.191.102.29', '2022-05-06 04:56:01'),
(166, 1, 'Member logged in.', '102.191.102.29', '2022-05-06 05:34:16'),
(167, 1, 'Member logged in.', '102.191.102.29', '2022-05-06 13:47:24'),
(168, 1, 'Member logged in.', '102.191.102.29', '2022-05-06 15:03:31'),
(169, 1, 'Member logged in.', '102.191.102.29', '2022-05-06 15:08:04'),
(170, 1, 'New support ticket created#8', '102.191.102.29', '2022-05-06 16:04:16'),
(171, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 16:47:52'),
(172, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 16:48:50'),
(173, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:06:36'),
(174, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:06:45'),
(175, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:12'),
(176, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:14'),
(177, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:16'),
(178, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:18'),
(179, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:20'),
(180, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:22'),
(181, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:24'),
(182, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:26'),
(183, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:29'),
(184, 1, 'Support request answered#8', '102.191.102.29', '2022-05-06 17:08:32'),
(185, 1, 'Support request answered#8', '102.191.201.47', '2022-05-06 20:28:10'),
(186, 1, 'New Child Panel Order with id : 4.', '102.191.201.47', '2022-05-06 20:39:16'),
(187, 1, 'API Key changed', '102.191.201.47', '2022-05-06 20:58:50'),
(188, 1, 'Member logged in.', '102.191.201.47', '2022-05-06 22:15:09'),
(189, 1, '0.07 New Order #16.', '102.191.201.47', '2022-05-06 22:30:52'),
(190, 36, '\r\n    User registered.', '196.151.138.71', '2022-05-06 23:52:49'),
(191, 36, 'Member logged in.', '196.151.138.71', '2022-05-06 23:58:35'),
(192, 37, '\r\n    User registered.', '41.233.190.145', '2022-05-07 16:33:37'),
(193, 1, 'Member logged in.', '102.191.164.156', '2022-05-07 17:30:05'),
(194, 1, 'Member logged in.', '102.191.164.156', '2022-05-07 17:33:46'),
(195, 1, 'Order has been canceled & Refund money for User#16', '102.191.164.156', '2022-05-07 17:33:58'),
(196, 1, 'Member logged in.', '105.196.30.214', '2022-05-09 23:00:05'),
(197, 38, '\r\n    User registered.', '196.152.72.45', '2022-05-10 15:40:51'),
(198, 1, 'Member logged in.', '105.196.221.64', '2022-05-11 16:10:55'),
(199, 2, 'Member logged in.', '102.47.194.194', '2022-05-11 16:12:59'),
(200, 2, 'Member logged in.', '105.196.149.126', '2022-05-11 20:29:11'),
(201, 39, '\r\n    User registered.', '196.129.111.168', '2022-05-15 04:35:06'),
(202, 14, 'Member logged in.', '156.199.46.81', '2022-05-16 13:27:03'),
(203, 1, 'Member logged in.', '102.191.205.165', '2022-05-18 21:35:06'),
(204, 1, 'Member logged in.', '105.196.231.154', '2022-05-20 13:44:03'),
(205, 1, 'Member logged in.', '105.196.231.154', '2022-05-21 14:06:47'),
(206, 2, 'Member logged in.', '105.196.231.154', '2022-05-21 23:01:45'),
(207, 40, '\r\n    User registered.', '196.150.200.12', '2022-05-21 23:02:30'),
(208, 36, 'Member logged in.', '41.68.204.121', '2022-05-21 23:29:47'),
(209, 1, 'Member logged in.', '105.196.231.154', '2022-05-22 00:17:53'),
(210, 1, 'Member logged in.', '105.196.231.154', '2022-05-22 00:18:30'),
(211, 41, '\r\n    User registered.', '156.210.221.42', '2022-05-22 00:33:21'),
(212, 42, '\r\n    User registered.', '157.37.196.34', '2022-07-17 08:45:53'),
(213, 42, 'Member logged in.', '157.39.154.76', '2022-07-17 09:09:01'),
(214, 42, 'Member logged in.', '47.31.171.191', '2022-07-17 11:27:59'),
(215, 42, 'Member logged in.', '157.39.154.76', '2022-07-17 14:33:11'),
(216, 42, 'Member logged in.', '157.39.154.76', '2022-07-17 16:54:01'),
(217, 42, 'Member logged in.', '157.39.30.62', '2022-07-17 17:06:33'),
(218, 42, 'Member logged in.', '157.39.30.62', '2022-07-17 17:19:20'),
(219, 42, 'Member logged in.', '157.39.30.62', '2022-07-17 17:21:25'),
(220, 42, 'Member logged in.', '157.39.30.62', '2022-07-17 17:23:26'),
(221, 42, 'Member logged in.', '157.39.30.62', '2022-07-17 17:26:00'),
(222, 43, '\r\n    User registered.', '182.176.147.67', '2022-07-18 11:08:03'),
(223, 42, 'Member logged in.', '157.39.41.58', '2022-07-18 15:59:47'),
(224, 44, '\r\n    User registered.', '111.119.187.35', '2022-07-18 20:05:02'),
(225, 45, '\r\n    User registered.', '37.111.242.116', '2022-07-19 07:31:41'),
(226, 46, '\r\n    User registered.', '157.38.136.171', '2022-07-19 08:20:40'),
(227, 47, '\r\n    User registered.', '115.87.128.27', '2022-07-29 17:03:53'),
(228, 42, 'Member logged in.', '47.31.225.181', '2022-07-29 17:33:04'),
(229, 47, 'Member logged in.', '115.87.128.27', '2022-07-30 11:36:12'),
(230, 48, '\r\n    User registered.', '47.31.198.61', '2022-07-30 12:16:38'),
(231, 47, 'New NAN  payment has been made with ', '203.151.205.45', '2022-07-30 12:33:19'),
(232, 47, 'New NAN  payment has been made with ', '203.151.205.45', '2022-07-30 13:00:26'),
(233, 47, 'New NAN  payment has been made with ', '203.151.205.33', '2022-07-30 13:02:07'),
(234, 47, 'New 0.27525461051473  payment has been made with ', '203.151.205.33', '2022-07-30 13:25:46'),
(235, 49, '\r\n    User registered.', '115.87.128.110', '2022-08-03 21:08:58'),
(236, 47, 'Member logged in.', '115.87.128.110', '2022-08-06 03:18:12'),
(237, 42, 'Member logged in.', '47.31.178.30', '2022-08-23 23:00:39'),
(238, 42, 'Member logged in.', '47.31.179.89', '2022-08-25 15:11:49'),
(239, 42, 'Member logged in.', '47.31.176.145', '2022-08-25 19:20:37'),
(240, 42, 'Member logged in.', '157.39.28.245', '2022-08-25 22:17:05'),
(241, 50, '\r\n    User registered.', '49.205.82.22', '2022-08-25 22:41:22'),
(242, 51, '\r\n    User registered.', '27.61.104.9', '2022-12-27 01:12:58'),
(243, 51, 'Member logged in.', '27.61.104.9', '2022-12-27 01:14:41'),
(244, 52, '\r\n    User registered.', '27.61.104.9', '2022-12-27 01:15:29'),
(245, 52, 'Member logged in.', '27.61.104.9', '2022-12-27 01:22:22'),
(246, 53, '\r\n    User registered.', '47.9.70.197', '2022-12-27 01:30:32'),
(247, 52, 'Member logged in.', '27.61.104.9', '2022-12-27 01:38:31'),
(248, 53, 'API Key changed', '27.63.17.59', '2022-12-27 07:20:52'),
(249, 51, 'Member logged in.', '27.61.104.9', '2022-12-27 10:48:08'),
(250, 51, 'Member logged in.', '27.61.104.9', '2022-12-27 12:50:24'),
(251, 54, '\r\n    User registered.', '49.42.36.61', '2022-12-27 12:59:08'),
(252, 51, 'Member logged in.', '27.61.104.9', '2022-12-27 13:10:10'),
(253, 51, 'Member logged in.', '27.61.104.9', '2022-12-27 13:23:06'),
(254, 48, 'Member logged in.', '27.61.104.9', '2022-12-27 13:57:51'),
(255, 51, 'Member logged in.', '27.61.104.9', '2022-12-27 16:04:50'),
(256, 54, 'API Key changed', '27.63.17.59', '2022-12-27 18:55:23'),
(257, 51, 'Member logged in.', '27.61.124.229', '2022-12-27 18:57:56'),
(258, 51, 'Member logged in.', '27.61.124.229', '2022-12-27 19:19:17'),
(259, 55, '\r\n    User registered.', '106.207.219.145', '2023-04-21 15:10:28'),
(260, 56, '\r\n    User registered.', '106.208.159.88', '2023-04-21 15:10:32'),
(261, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 15:27:24'),
(262, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 16:09:51'),
(263, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 16:16:24'),
(264, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 16:32:39'),
(265, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 17:13:15'),
(266, 55, '1 New Order #17.', '106.208.182.82', '2023-04-21 19:01:00'),
(267, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 19:07:02'),
(268, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 19:29:49'),
(269, 56, 'Member logged in.', '106.208.159.88', '2023-04-21 22:20:41'),
(270, 55, 'Member logged in.', '106.208.170.228', '2023-04-22 13:16:15'),
(271, 55, 'Member logged in.', '106.208.171.123', '2023-04-22 13:22:36'),
(272, 55, 'Member logged in.', '106.208.171.123', '2023-04-22 13:25:04'),
(273, 55, 'Member logged in.', '106.207.217.86', '2023-04-22 20:21:21'),
(274, 57, '\r\n    User registered.', '103.173.124.163', '2023-04-23 16:39:10'),
(275, 56, 'Member logged in.', '117.98.58.144', '2023-04-23 17:47:21'),
(276, 55, 'API Key changed', '106.207.229.27', '2023-04-23 18:58:35'),
(277, 58, '\r\n    User registered.', '27.62.235.135', '2023-04-24 19:22:12'),
(278, 58, 'Member logged in.', '27.62.235.135', '2023-04-24 19:24:00'),
(279, 58, 'Member logged in.', '27.62.235.135', '2023-04-24 20:06:07'),
(280, 56, 'Member logged in.', '106.205.25.116', '2023-04-24 22:14:55'),
(281, 56, 'Member logged in.', '106.205.25.116', '2023-04-24 22:22:17'),
(282, 59, '\r\n    User registered.', '49.36.237.138', '2023-04-24 23:03:35'),
(283, 55, 'Member logged in.', '27.62.246.77', '2023-04-24 23:15:53'),
(284, 56, 'Member logged in.', '27.60.63.103', '2023-04-25 08:30:23'),
(285, 60, '\r\n    User registered.', '27.60.63.103', '2023-04-25 11:41:32'),
(286, 56, 'Member logged in.', '27.60.63.103', '2023-04-25 11:48:10'),
(287, 56, 'Member logged in.', '27.60.63.103', '2023-04-25 14:25:14'),
(288, 56, 'Member logged in.', '27.60.63.103', '2023-04-25 22:01:09'),
(289, 55, 'Member logged in.', '27.56.206.166', '2023-04-26 09:04:05'),
(290, 61, '\r\n    User registered.', '103.127.224.237', '2023-04-28 18:43:39'),
(291, 56, 'Member logged in.', '171.76.224.68', '2023-04-28 22:52:30'),
(292, 56, 'Member logged in.', '171.76.224.68', '2023-04-28 22:56:21'),
(293, 62, '\r\n    User registered.', '103.16.25.243', '2023-05-01 12:20:37'),
(294, 55, 'Member logged in.', '106.194.136.91', '2023-05-01 12:49:25'),
(295, 63, '\r\n    User registered.', '117.205.72.147', '2023-05-01 12:54:19'),
(296, 63, '0 New Order #18.', '117.205.72.147', '2023-05-01 12:57:24'),
(297, 63, '0 New Order #19.', '117.205.72.147', '2023-05-01 13:01:45'),
(298, 63, '0 New Order #20.', '117.205.72.147', '2023-05-01 13:03:00'),
(299, 64, '\r\n    User registered.', '42.106.182.120', '2023-05-06 07:46:19'),
(300, 65, '\r\n    User registered.', '42.106.176.185', '2023-05-12 01:39:40'),
(301, 55, 'Member logged in.', '49.35.194.247', '2023-05-13 09:31:38'),
(302, 66, '\r\n    User registered.', '106.197.179.158', '2023-05-22 07:24:53'),
(303, 67, '\r\n    User registered.', '103.69.94.36', '2024-03-17 04:54:16'),
(304, 68, '\r\n    User registered.', '103.106.239.237', '2024-03-17 04:59:47'),
(305, 68, 'API Key changed', '103.106.239.237', '2024-03-17 05:01:45');

-- --------------------------------------------------------

--
-- Table structure for table `currency`
--

CREATE TABLE `currency` (
  `id` int(11) NOT NULL,
  `symbol` text DEFAULT NULL,
  `value` double DEFAULT NULL,
  `name` varchar(225) NOT NULL,
  `status` enum('1','2') NOT NULL DEFAULT '1',
  `default` enum('2','1') NOT NULL DEFAULT '2',
  `nouse` enum('1','2') NOT NULL DEFAULT '2'
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `currency`
--

INSERT INTO `currency` (`id`, `symbol`, `value`, `name`, `status`, `default`, `nouse`) VALUES
(1, '$', 1, 'USD', '1', '1', '1'),
(7, '฿', 36.33, 'Baht', '1', '2', '2'),
(8, '₹', 79, 'INR', '1', '2', '2');

-- --------------------------------------------------------

--
-- Table structure for table `earn`
--

CREATE TABLE `earn` (
  `earn_id` int(255) NOT NULL,
  `client_id` int(255) NOT NULL,
  `link` text NOT NULL,
  `earn_note` text NOT NULL,
  `status` enum('Pending','Under Review','Funds Granted','Rejected','Not Eligible') NOT NULL DEFAULT 'Pending'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `earn`
--

INSERT INTO `earn` (`earn_id`, `client_id`, `link`, `earn_note`, `status`) VALUES
(1, 41, 'https://demo.wixout.com/', '', 'Pending');

-- --------------------------------------------------------

--
-- Table structure for table `files`
--

CREATE TABLE `files` (
  `id` int(11) NOT NULL,
  `link` text DEFAULT NULL,
  `date` datetime NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `General_options`
--

CREATE TABLE `General_options` (
  `id` int(11) NOT NULL,
  `coupon_status` enum('1','2') NOT NULL DEFAULT '1',
  `updates_show` enum('1','2') NOT NULL DEFAULT '1',
  `panel_status` enum('Pending','Active','Frozen','Suspended') NOT NULL,
  `panel_orders` int(11) NOT NULL,
  `panel_thismonthorders` int(11) NOT NULL,
  `massorder` enum('1','2') NOT NULL DEFAULT '2',
  `balance_format` enum('0.0','0.00','0.000','0.0000') NOT NULL DEFAULT '0.0',
  `currency_format` enum('0','2','3','4') NOT NULL DEFAULT '3',
  `ticket_system` enum('1','2') NOT NULL DEFAULT '1'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_unicode_ci;

--
-- Dumping data for table `General_options`
--

INSERT INTO `General_options` (`id`, `coupon_status`, `updates_show`, `panel_status`, `panel_orders`, `panel_thismonthorders`, `massorder`, `balance_format`, `currency_format`, `ticket_system`) VALUES
(1, '', '2', 'Active', 1024, 20, '1', '', '2', '2');

-- --------------------------------------------------------

--
-- Table structure for table `integrations`
--

CREATE TABLE `integrations` (
  `id` int(11) NOT NULL,
  `name` varchar(225) NOT NULL,
  `description` varchar(225) NOT NULL,
  `icon_url` varchar(225) NOT NULL,
  `code` text NOT NULL,
  `visibility` int(11) NOT NULL,
  `status` int(11) NOT NULL DEFAULT 1
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `integrations`
--

INSERT INTO `integrations` (`id`, `name`, `description`, `icon_url`, `code`, `visibility`, `status`) VALUES
(1, 'Beamer', 'Announce updates and get feedback with in-app notification center, widgets and changelog', '/img/integrations/Beamer.svg', '', 1, 1),
(2, 'Getsitecontrol', 'It helps you prevent website visitors from leaving your website without taking any action.', '/img/integrations/Getsitecontrol.svg', '', 1, 1),
(3, 'Google Analytics', 'Statistics and basic analytical tools for search engine optimization (SEO) and marketing purposes', '/img/integrations/Google%20Analytics.svg', '', 1, 2),
(4, 'Google Tag manager', 'Manage all your website tags without editing the code using simple tag management solutions', '/img/integrations/Google%20Tag%20manager.svg', '', 1, 1),
(5, 'JivoChat', 'All-in-one business messenger to talk to customers: live chat, phone, email and social', '/img/integrations/JivoChat.svg', '', 1, 1),
(6, 'Onesignal', 'Leader in customer engagement, empowers mobile push, web push, email, in-app messages', '/img/integrations/Onesignal.svg', '', 1, 1),
(7, 'Push alert', 'Increase reach, revenue, retarget users with Push Notifications on desktop and mobile', '/img/integrations/Push%20alert.svg', '', 1, 1),
(8, 'Smartsupp', 'Live chat, email inbox and Facebook Messenger in one customer messaging platform', '/img/integrations/Smartsupp.svg', '', 1, 1),
(9, 'Tawk.to', 'Track and chat with visitors on your website, mobile app or a free customizable page', '/img/integrations/Tawk.to.svg', '', 1, 1),
(10, 'Tidio', 'Communicator for businesses that keep live chat, chatbots, Messenger and email in one place', '/img/integrations/Tidio.svg', '', 1, 1),
(11, 'Zendesk Chat', 'Helps respond quickly to customer questions, reduce wait times and increase sales', '/img/integrations/Zendesk%20Chat.svg', '', 1, 1),
(12, 'Getbutton.io', 'Chat with website visitors through popular messaging apps. Whatsapp, messenger etc. contact button.', '/img/integrations/Getbutton.svg', '', 1, 1),
(13, 'Google reCAPTCHA v2', 'It uses an advanced risk analysis engine and adaptive challenges to prevent malware from engaging in abusive activities on your website.', '/img/integrations/reCAPTCHA.svg', '', 1, 1),
(14, 'Whatsapp', 'Whatsapp is for Personal Support of your Users', '/img/integrations/whatsapp.svg', '', 1, 2);

-- --------------------------------------------------------

--
-- Table structure for table `kuponlar`
--

CREATE TABLE `kuponlar` (
  `id` int(11) NOT NULL,
  `kuponadi` varchar(255) NOT NULL,
  `adet` int(11) NOT NULL,
  `tutar` double NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_swedish_ci;

-- --------------------------------------------------------

--
-- Table structure for table `kupon_kullananlar`
--

CREATE TABLE `kupon_kullananlar` (
  `id` int(11) NOT NULL,
  `uye_id` int(11) NOT NULL,
  `kuponadi` varchar(255) NOT NULL,
  `tutar` double NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_swedish_ci;

-- --------------------------------------------------------

--
-- Table structure for table `languages`
--

CREATE TABLE `languages` (
  `id` int(11) NOT NULL,
  `language_name` varchar(225) NOT NULL,
  `language_code` varchar(225) NOT NULL,
  `language_type` enum('2','1') NOT NULL DEFAULT '2',
  `default_language` enum('0','1') NOT NULL DEFAULT '0'
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `languages`
--

INSERT INTO `languages` (`id`, `language_name`, `language_code`, `language_type`, `default_language`) VALUES
(1, 'English', 'en', '2', '1'),
(4, 'arabic', 'ar', '1', '0');

-- --------------------------------------------------------

--
-- Table structure for table `Mailforms`
--

CREATE TABLE `Mailforms` (
  `id` int(11) NOT NULL,
  `subject` varchar(225) NOT NULL,
  `message` varchar(225) NOT NULL,
  `status` enum('1','2') NOT NULL DEFAULT '1',
  `header` varchar(225) NOT NULL,
  `footer` varchar(225) NOT NULL,
  `type` enum('Admins','Users') NOT NULL DEFAULT 'Users'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `menus`
--

CREATE TABLE `menus` (
  `id` int(11) NOT NULL,
  `name` text NOT NULL,
  `menu_line` double NOT NULL,
  `type` enum('1','2') CHARACTER SET utf8mb3 COLLATE utf8mb3_general_ci NOT NULL DEFAULT '2',
  `slug` varchar(225) NOT NULL DEFAULT '2',
  `icon` varchar(225) DEFAULT NULL,
  `menu_status` enum('1','2') CHARACTER SET utf8mb3 COLLATE utf8mb3_general_ci NOT NULL DEFAULT '1',
  `visible` enum('Internal','External') NOT NULL DEFAULT 'Internal',
  `active` varchar(225) NOT NULL,
  `tiptext` varchar(225) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_bin;

--
-- Dumping data for table `menus`
--

INSERT INTO `menus` (`id`, `name`, `menu_line`, `type`, `slug`, `icon`, `menu_status`, `visible`, `active`, `tiptext`) VALUES
(1, 'New Order', 1, '2', '/', 'fas fa-cart-arrow-down', '1', 'Internal', 'neworder', ''),
(2, 'Mass Order', 2, '1', '/massorder', 'fas fa-cart-plus', '1', 'Internal', 'massorder', 'Shown only if Mass Order system enabled for use'),
(3, 'My Orders ', 3, '2', '/orders', 'fas fa-briefcase', '1', 'Internal', 'orders', ''),
(4, 'Refill', 5, '2', '/refill', 'fas fa-recycle', '1', 'Internal', 'refill', 'Shown only if user have at least one refill task'),
(5, 'Login', 2, '2', '/', 'fas fa-sign-in-alt', '1', 'External', 'login', ''),
(6, 'Services', 6, '2', '/services', 'fas fa-bars', '1', 'Internal', 'services', ''),
(7, 'Add Funds', 7, '2', '/addfunds', 'fas fa-rupee-sign', '1', 'Internal', 'addfunds', ''),
(9, 'Tickets / Request', 9, '2', '/tickets', 'fas fa-headset', '1', 'Internal', 'tickets', ''),
(41, 'Child Panels', 10, '2', '/child-panels', 'fas fa-child', '1', 'Internal', 'childpanels', ''),
(11, 'Affiliates', 8, '2', '/refer', 'far fa-share-square', '1', 'Internal', 'refer', 'Shown only if affiliate system enabled for use'),
(15, 'Api', 4, '2', '/api', 'fas fa-code', '1', 'External', 'api', ''),
(18, 'Services', 5, '2', '/services', 'fas fa-bars', '1', 'External', 'terms', ''),
(49, 'Dashboard', 15, '2', '/Dashboard', 'fas fa-code', '1', 'Internal', 'Dashboard', ''),
(29, 'Blogs', 6, '2', '/blog', 'fas fa-blog', '1', 'External', 'blog', ''),
(46, 'Rules / Terms', 14, '2', '/terms', 'fas fa-exclamation-triangle', '1', 'Internal', 'transferfunds', ''),
(48, 'User Api', 15, '2', '/api', 'fas fa-code', '1', 'Internal', 'api', '');

-- --------------------------------------------------------

--
-- Table structure for table `news`
--

CREATE TABLE `news` (
  `id` int(11) NOT NULL,
  `news_icon` varchar(225) NOT NULL,
  `news_title` varchar(225) NOT NULL,
  `news_content` varchar(225) NOT NULL,
  `news_date` datetime NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `notifications_popup`
--

CREATE TABLE `notifications_popup` (
  `id` int(11) NOT NULL,
  `title` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `action_link` text NOT NULL,
  `isAllPage` enum('0','1') NOT NULL DEFAULT '0',
  `isAllUser` enum('1','0') NOT NULL DEFAULT '0',
  `expiry_date` date NOT NULL,
  `status` enum('1','2','0') NOT NULL DEFAULT '1',
  `allPages` varchar(225) NOT NULL,
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `action_text` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `orders`
--

CREATE TABLE `orders` (
  `order_id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `service_id` int(11) NOT NULL,
  `api_orderid` int(11) NOT NULL DEFAULT 0,
  `order_error` text NOT NULL,
  `order_detail` text DEFAULT NULL,
  `order_api` int(11) NOT NULL DEFAULT 0,
  `api_serviceid` int(11) NOT NULL DEFAULT 0,
  `api_charge` double NOT NULL DEFAULT 0,
  `api_currencycharge` double DEFAULT 1,
  `order_profit` double NOT NULL,
  `order_quantity` double NOT NULL,
  `order_extras` text NOT NULL,
  `order_charge` double NOT NULL,
  `dripfeed` enum('1','2','3') DEFAULT '1' COMMENT '2 -> ON, 1 -> OFF',
  `dripfeed_id` double NOT NULL DEFAULT 0,
  `subscriptions_id` double NOT NULL DEFAULT 0,
  `subscriptions_type` enum('1','2') NOT NULL DEFAULT '1' COMMENT '2 -> ON, 1 -> OFF',
  `dripfeed_totalcharges` double DEFAULT NULL,
  `dripfeed_runs` double DEFAULT NULL,
  `dripfeed_delivery` double NOT NULL DEFAULT 0,
  `dripfeed_interval` double DEFAULT NULL,
  `dripfeed_totalquantity` double DEFAULT NULL,
  `dripfeed_status` enum('active','completed','canceled') NOT NULL DEFAULT 'active',
  `order_url` text NOT NULL,
  `order_start` double NOT NULL DEFAULT 0,
  `order_finish` double NOT NULL DEFAULT 0,
  `order_remains` double NOT NULL DEFAULT 0,
  `order_create` datetime NOT NULL,
  `order_status` enum('pending','inprogress','completed','partial','processing','canceled') NOT NULL DEFAULT 'pending',
  `subscriptions_status` enum('active','paused','completed','canceled','expired','limit') NOT NULL DEFAULT 'active',
  `subscriptions_username` text DEFAULT NULL,
  `subscriptions_posts` double DEFAULT NULL,
  `subscriptions_delivery` double NOT NULL DEFAULT 0,
  `subscriptions_delay` double DEFAULT NULL,
  `subscriptions_min` double DEFAULT NULL,
  `subscriptions_max` double DEFAULT NULL,
  `subscriptions_expiry` date DEFAULT NULL,
  `last_check` datetime NOT NULL,
  `order_where` enum('site','api') NOT NULL DEFAULT 'site',
  `refill_status` enum('Pending','Refilling','Completed','Rejected','Error') NOT NULL DEFAULT 'Pending',
  `is_refill` enum('1','2') NOT NULL DEFAULT '1',
  `refill` varchar(225) NOT NULL DEFAULT '1',
  `cancelbutton` enum('1','2') NOT NULL DEFAULT '1' COMMENT '1 -> ON, 2 -> OFF',
  `show_refill` enum('true','false') NOT NULL DEFAULT 'true',
  `api_refillid` double NOT NULL DEFAULT 0,
  `avg_done` enum('0','1') NOT NULL DEFAULT '1',
  `order_increase` int(11) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `orders`
--

INSERT INTO `orders` (`order_id`, `client_id`, `service_id`, `api_orderid`, `order_error`, `order_detail`, `order_api`, `api_serviceid`, `api_charge`, `api_currencycharge`, `order_profit`, `order_quantity`, `order_extras`, `order_charge`, `dripfeed`, `dripfeed_id`, `subscriptions_id`, `subscriptions_type`, `dripfeed_totalcharges`, `dripfeed_runs`, `dripfeed_delivery`, `dripfeed_interval`, `dripfeed_totalquantity`, `dripfeed_status`, `order_url`, `order_start`, `order_finish`, `order_remains`, `order_create`, `order_status`, `subscriptions_status`, `subscriptions_username`, `subscriptions_posts`, `subscriptions_delivery`, `subscriptions_delay`, `subscriptions_min`, `subscriptions_max`, `subscriptions_expiry`, `last_check`, `order_where`, `refill_status`, `is_refill`, `refill`, `cancelbutton`, `show_refill`, `api_refillid`, `avg_done`, `order_increase`) VALUES
(1, 2, 1, 0, '-', NULL, 0, 0, 0, 1, 0, 1000, '', 0, '1', 0, 0, '1', NULL, NULL, 0, NULL, NULL, 'active', 'fdfdsf', 0, 0, 0, '2022-04-23 21:39:08', 'pending', 'active', NULL, NULL, 0, NULL, NULL, NULL, NULL, '2022-04-23 21:39:08', 'site', 'Pending', '1', '1', '1', 'true', 0, '1', 0),
(17, 55, 5297, 0, '-', NULL, 0, 0, 0, 1, 1, 1000, '', 1, '1', 0, 0, '1', NULL, NULL, 0, NULL, NULL, 'active', 'https://instagram.com/babu_bhai_307__?igshid=YmMyMTA2M2Y=', 0, 0, 0, '2023-04-21 19:01:00', 'pending', 'active', NULL, NULL, 0, NULL, NULL, NULL, NULL, '2023-04-21 19:01:00', 'site', 'Pending', '1', '1', '1', 'true', 0, '1', 0),
(18, 63, 5600, 415546, '-', '{\"order\":415546}', 12, 463, 0.0959, NULL, -0.0959, 1000, '', 0, '1', 0, 0, '1', NULL, NULL, 0, NULL, NULL, 'active', 'https://vt.tiktok.com/ZS8vcP4xj', 0, 0, 0, '2023-05-01 12:57:24', 'pending', 'active', '', 0, 0, 0, 0, 0, '1970-01-01', '2023-05-01 12:57:24', 'site', 'Pending', '1', '1', '1', 'true', 0, '1', 0),
(19, 63, 5601, 0, '{\"error\":\"You are out of balance. Please recharge your balance to send order with quantity: 100000 for service id: 480\"}', '{\"error\":\"You are out of balance. Please recharge your balance to send order with quantity: 100000 for service id: 480\"}', 12, 480, 0, NULL, 0, 100000, '', 0, '1', 0, 0, '1', NULL, NULL, 0, NULL, NULL, 'active', 'https://vt.tiktok.com/ZS8ToDh4F', 0, 0, 0, '2023-05-01 13:01:44', 'pending', 'active', '', 0, 0, 0, 0, 0, '1970-01-01', '2023-05-01 13:01:44', 'site', 'Pending', '1', '1', '1', 'true', 0, '1', 0),
(20, 63, 5600, 0, '{\"error\":\"You are out of balance. Please recharge your balance to send order with quantity: 100000 for service id: 463\"}', '{\"error\":\"You are out of balance. Please recharge your balance to send order with quantity: 100000 for service id: 463\"}', 12, 463, 0, NULL, 0, 100000, '', 0, '1', 0, 0, '1', NULL, NULL, 0, NULL, NULL, 'active', 'https://vt.tiktok.com/ZS8ToV51m', 0, 0, 0, '2023-05-01 13:03:00', 'pending', 'active', '', 0, 0, 0, 0, 0, '1970-01-01', '2023-05-01 13:03:00', 'site', 'Pending', '1', '1', '1', 'true', 0, '1', 0);

-- --------------------------------------------------------

--
-- Table structure for table `pages`
--

CREATE TABLE `pages` (
  `page_id` int(11) NOT NULL,
  `page_name` varchar(225) NOT NULL,
  `page_get` varchar(225) NOT NULL,
  `page_content` text NOT NULL,
  `page_status` enum('1','2') NOT NULL DEFAULT '1',
  `active` enum('1','2') NOT NULL DEFAULT '1',
  `seo_title` varchar(225) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `seo_keywords` varchar(225) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `seo_description` varchar(225) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `last_modified` datetime NOT NULL,
  `del` varchar(255) NOT NULL DEFAULT '1',
  `page_content2` text NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `pages`
--

INSERT INTO `pages` (`page_id`, `page_name`, `page_get`, `page_content`, `page_status`, `active`, `seo_title`, `seo_keywords`, `seo_description`, `last_modified`, `del`, `page_content2`) VALUES
(2, 'Add funds', 'addfunds', '', '1', '1', '', '', '', '2023-04-21 10:29:17', '2', ''),
(787, 'Login', 'auth', '', '1', '1', 'Best Smm Panel', '', '', '2022-07-17 02:15:43', '2', ''),
(9, 'New Order', 'neworder', '❤We Can\'t cancel after placing an order/check URL before Order ❤\r\n❤ If you don\'t know how to Order Pls Contact us Before Order We Are Support You / do not Order the wrong URL with ❤ \r\n?Do not add duplicate order if your first order Running\r\nRead T&C Before Order Thank You ❤\r\nSmartestsmm.Com ', '1', '1', '', '', '', '2023-04-25 12:33:41', '2', '    <div style=\"text-align: center;\"><span style=\"color: rgb(0, 0, 0); font-family: georgia; text-align: start; background-color: rgb(255, 255, 255);\"><font size=\"2\"><br></font></span></div><div style=\"text-align: center;\"><span style=\"color: rgb(0, 0, 0); font-family: georgia; text-align: start; background-color: rgb(255, 255, 255);\"><font size=\"2\"><br></font></span></div><div style=\"text-align: center;\"><span style=\"color: rgb(0, 0, 0); font-family: georgia; text-align: start; background-color: rgb(255, 255, 255);\"><font size=\"2\">❤We Can\'t cancel after placing an order/check URL before Order ❤</font></span><br></div><div style=\"text-align: center;\"><span style=\"color: rgb(0, 0, 0); font-family: georgia; text-align: start; background-color: rgb(255, 255, 255);\"><font size=\"2\">❤ If you don\'t know how to Order Pls Contact us </font></span><span style=\"color: rgb(0, 0, 0); font-family: georgia; font-size: small;\">Before</span><span style=\"font-size: small; color: rgb(0, 0, 0); font-family: georgia; text-align: start;\"> Order We Are Support You / do not Order the wrong URL with ❤ </span></div><div style=\"text-align: center;\"><span style=\"text-align: start;\"><font color=\"#000000\" face=\"georgia\" size=\"2\">?Do not add duplicate order if your first order Running</font><br></span></div><div style=\"text-align: center;\"><span style=\"font-size: small; font-family: georgia; text-align: start;\"><font color=\"#ff0000\">Read T&C Before Order Thank You ❤</font></span></div><div style=\"text-align: center;\"><span style=\"font-size: small; font-family: georgia; text-align: start;\"><font color=\"#ff0000\">Smartestsmm.com </font></span></div>\r\n        </div>'),
(14, 'Terms', 'terms', '<div>\r\n  <div>\r\n<h2><b>Terms and Conditions</b></h2>\r\n<h5>By registering or using our services you agree that you have read and fully understood the following terms of Service and SMMSQUID.COM will not be help liable for loss in any way for users who have not read the below terms of service.</h5>\r\n</div>\r\n\r\n<h2><b>Important Rules</b></h2>\r\n<h5>✅   You will only use the website in a manner which follows all agreements made with Instagram/facebook/twitter/youtube/other social media site on their individual Terms of Service page<br><br>\r\n\r\n✅  SMMSQUID.COM will only be used to promote your Telegram/Instagram/Twitter/Facebook and Other Social Profiles for Personal engagements and to increase your Social Effectiveness.<br><br>\r\n\r\n✅  Do not use two services at the same time for Same Link. If you do this, we will not be able to fix it. Wait for the first order to be completed, then place new order for the same link.<br><br>\r\n\r\n✅  There is no possibility of refund after charging the account in our panel.<br><br>\r\n\r\n✅  Use only the tickets section for support<br><br>\r\n\r\n✅   It is not possible to cancel the order after Start. Unless you have a good reason for it.<br><br>\r\n\r\n✅   We terminate accounts without any notice if a user without any orders/deposits for more than 3 months since registered.<br><br>\r\n\r\n✅   SMMSQUID.COM does not guarantee a delivery time for any services. We offer our best estimation for when the order will be delivered.<br></h5>\r\n\r\n<h2><b>Privacy Policy</b></h2>\r\n<h5>This page informs you of our policies regarding the collection, use, and disclosure of personal data when you use our Service and the choices you have associated with that data.<br><br>\r\n\r\nWe use your data to provide and improve the Service. By using the Service, you agree to the collection and use of information in accordance with this policy. Unless otherwise defined in this Privacy Policy, terms used in this Privacy Policy have the same meanings as in our Terms and Conditions, accessible from https://SMMSQUID.COM<br><br>\r\n</h5><br>\r\n\r\n<h2><b>Tracking and Cookies Data</b></h2>\r\n<h5>We use cookies and similar tracking technologies to track the activity on our Service and hold certain information.<br><br>\r\n\r\nCookies are files with small amount of data which may include an anonymous unique identifier. Cookies are sent to your browser from a website and stored on your device. Tracking technologies also used are beacons, tags, and scripts to collect and track information and to improve and analyze our Service.<br><br>\r\n\r\nYou can instruct your browser to refuse all cookies or to indicate when a cookie is being sent. However, if you do not accept cookies, you may not be able to use some portions of our Service.<br><br>\r\n\r\n<h4>Examples of Cookies we use:</h4>\r\nSession Cookies. We use Session Cookies to operate our Service.<br>\r\nPreference Cookies. We use Preference Cookies to remember your preferences and various settings.<br>\r\nSecurity Cookies. We use Security Cookies for security purposes.<br>\r\n<h4>Use of Data</h4>\r\nSMMSQUID.COM uses the collected data for various purposes:\r\n<ul>\r\n<li>To provide and maintain the Service</li>\r\n<li>To notify you about changes to our Service</li>\r\n<li>To allow you to participate in interactive features of our Service when you choose to do so</li>\r\n<li>To provide customer care and support</li>\r\n<li>To provide analysis or valuable information so that we can improve the Service</li>\r\n<li>To monitor the usage of the Service</li>\r\n</ul>\r\n<div>', '1', '1', '', '', '', '2022-12-27 02:46:21', '2', ''),
(789, 'Mass Order', 'massorder', '', '2', '1', '', '', '', '2022-02-07 08:43:06', '2', ''),
(790, 'Orders', 'orders', '', '1', '1', '', '', '', '2022-02-07 08:53:20', '2', ''),
(791, 'Services', 'services', '', '1', '1', '', '', '', '2022-01-26 07:22:09', '2', ''),
(792, 'Tickets', 'tickets', '<center><h4>If you are looking for a specific service that you can not find in our panel, in this section you can request it.<br><br>\r\n\r\nRaise a Request Service ticket below and explain what kind of service you need.<br><br>\r\n\r\n\r\n<b>We will prepare it for you soon..!</b></h4>\r\n</center>', '1', '1', '', '', '', '2022-12-27 02:55:06', '2', ''),
(793, 'API', 'api', '', '1', '1', '', '', '', '2022-01-24 07:21:07', '2', ''),
(794, 'Signup', 'signup', '', '1', '1', '', '', '', '2022-01-24 07:21:07', '2', ''),
(795, 'Blog', 'blog', '', '1', '1', '', '', '', '2022-01-24 07:21:07', '2', '');

-- --------------------------------------------------------

--
-- Table structure for table `panel_categories`
--

CREATE TABLE `panel_categories` (
  `id` int(11) NOT NULL,
  `name` text CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `status` enum('0','1') NOT NULL DEFAULT '1' COMMENT '1 -> ENABLE, 0 -> DISABLE'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `panel_info`
--

CREATE TABLE `panel_info` (
  `panel_id` int(11) NOT NULL,
  `panel_domain` text NOT NULL,
  `panel_plan` text NOT NULL,
  `panel_status` enum('Pending','Active','Frozen','Suspended') NOT NULL,
  `panel_orders` int(11) NOT NULL,
  `panel_thismonthorders` int(11) NOT NULL,
  `date_created` datetime NOT NULL,
  `api_key` varchar(225) NOT NULL,
  `renewal_date` datetime NOT NULL,
  `panel_type` enum('Child','Main') NOT NULL DEFAULT 'Main'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_unicode_ci;

--
-- Dumping data for table `panel_info`
--

INSERT INTO `panel_info` (`panel_id`, `panel_domain`, `panel_plan`, `panel_status`, `panel_orders`, `panel_thismonthorders`, `date_created`, `api_key`, `renewal_date`, `panel_type`) VALUES
(1, 'yourpanel.com', 'A', 'Active', 1395, 1395, '2022-01-24 10:58:08', 'b1fbedd6f1266a8990bf648919068680', '2025-02-23 10:58:08', 'Main');

-- --------------------------------------------------------

--
-- Table structure for table `payments`
--

CREATE TABLE `payments` (
  `payment_id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `client_balance` decimal(15,2) NOT NULL DEFAULT 0.00,
  `payment_amount` decimal(15,4) NOT NULL,
  `payment_privatecode` double DEFAULT NULL,
  `payment_method` int(11) NOT NULL,
  `payment_status` enum('1','2','3') NOT NULL DEFAULT '1',
  `payment_delivery` enum('1','2') NOT NULL DEFAULT '1',
  `payment_note` varchar(255) NOT NULL DEFAULT 'No',
  `payment_mode` enum('Manuel','Otomatik','Auto') NOT NULL DEFAULT 'Otomatik',
  `payment_create_date` datetime NOT NULL,
  `payment_update_date` datetime NOT NULL,
  `payment_ip` varchar(225) NOT NULL,
  `payment_extra` text NOT NULL,
  `payment_bank` int(11) NOT NULL,
  `t_id` varchar(255) DEFAULT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `payments`
--

INSERT INTO `payments` (`payment_id`, `client_id`, `client_balance`, `payment_amount`, `payment_privatecode`, `payment_method`, `payment_status`, `payment_delivery`, `payment_note`, `payment_mode`, `payment_create_date`, `payment_update_date`, `payment_ip`, `payment_extra`, `payment_bank`, `t_id`) VALUES
(119, 55, 0.00, 10.0000, NULL, 1, '3', '2', 'No', 'Manuel', '2023-04-21 17:17:10', '2023-04-21 17:17:10', '', '', 0, NULL),
(120, 55, 10.00, 10.0000, NULL, 1, '3', '2', 'No', 'Manuel', '2023-04-21 17:17:18', '2023-04-21 17:17:18', '', '', 0, NULL),
(121, 68, 0.00, 0.2671, NULL, 12, '1', '1', 'No', 'Auto', '2024-03-17 05:10:39', '0000-00-00 00:00:00', '103.106.239.237', 'b0275967146ea7df338f29558615ab01', 0, NULL),
(122, 68, 0.00, 20.0000, NULL, 2, '1', '1', 'No', 'Auto', '2024-03-17 05:10:56', '0000-00-00 00:00:00', '103.106.239.237', 'abe2ca61c029b13e9be6d6fc73c75986', 0, NULL);

-- --------------------------------------------------------

--
-- Table structure for table `payments_bonus`
--

CREATE TABLE `payments_bonus` (
  `bonus_id` int(11) NOT NULL,
  `bonus_method` int(11) NOT NULL,
  `bonus_from` double NOT NULL,
  `bonus_amount` double NOT NULL,
  `bonus_type` enum('1','2') NOT NULL DEFAULT '2'
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `payment_methods`
--

CREATE TABLE `payment_methods` (
  `id` int(11) NOT NULL,
  `method_name` varchar(225) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `method_get` varchar(225) NOT NULL,
  `method_min` double NOT NULL,
  `method_max` double NOT NULL,
  `method_type` enum('1','2') NOT NULL DEFAULT '2' COMMENT '2 -> ON, 1 -> OFF	',
  `method_extras` text NOT NULL,
  `method_line` double NOT NULL,
  `nouse` enum('1','2') NOT NULL DEFAULT '2',
  `content` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `payment_methods`
--

INSERT INTO `payment_methods` (`id`, `method_name`, `method_get`, `method_min`, `method_max`, `method_type`, `method_extras`, `method_line`, `nouse`, `content`) VALUES
(1, 'Paypal', 'paypal', 10, 10000, '2', '{\"method_type\":\"2\",\"name\":\"Paypal ( USD ) ( International Payments ) [ 10% Charge ]\",\"min\":\"10\",\"max\":\"10000\",\"client_id\":\"AR3wtI3dxA0qU2dme-kQdC6csRL4whF8SNWzJ2jilchyZvQsBJ7URF4UqktveDp67guIenYYX-e0zuCz\",\"client_secret\":\"EMFtatHjrBMf9EYcec0WZqKwGwO2aum03w62b9tZZWPB2G__WoFuBMkMu0z97NR8ooRJNXR0FqrtagrD\",\"fee\":\"10\"}', 6, '2', 'hello'),
(2, 'Stripe', 'stripe', 1, 100, '2', '{\"method_type\":\"2\",\"name\":\"Credit card\\/ Debit cards \\/Meeza cards\\/Mobile Wallets (5%BONUS FROM 10$)(Ramdan Offer)\",\"min\":\"1\",\"max\":\"100\",\"stripe_publishable_key\":\"pk_live_51HiUnRLjkQAtcIW0F983imoO8qhftSSMSj7oB9xTjGHB51su6vnuDmGNs5l2NNZz1XE1Ogf1svxqjtdasRYr3atk00wEAHHKNT\",\"stripe_secret_key\":\"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\",\"stripe_webhooks_secret\":\"whsec_gSvhMz0eOIOTk5S9uzzzDgpHeclOmiDe\",\"fee\":\"10\",\"currency\":\"USD\"}', 3, '2', ''),
(3, 'Shopier', 'shopier', 5, 0, '1', '{\"method_type\":\"1\",\"name\":\"Kredi \\/ Banka Kart\\u0131 ile \\u00d6de\",\"min\":\"5\",\"max\":\"0\",\"apiKey\":\"\",\"apiSecret\":\"\",\"website_index\":\"1\",\"processing_fee\":\"1\",\"fee\":\"10\",\"currency\":\"USD\"}', 12, '2', ''),
(5, 'Paywant', 'paywant', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Paywant\",\"min\":\"1\",\"max\":\"0\",\"apiKey\":\"\",\"apiSecret\":\"\",\"fee\":\"0\",\"currency\":\"USD\",\"commissionType\":\"2\",\"payment_type\":[\"1\",\"2\",\"3\"]}', 13, '2', ''),
(7, 'PayTR', 'paytr', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Paytr\",\"min\":\"1\",\"max\":\"0\",\"merchant_id\":\"\",\"merchant_key\":\"\",\"merchant_salt\":\"\",\"fee\":\"0\",\"currency\":\"USD\"}', 14, '2', ''),
(8, 'Coinpayments', 'coinpayments', 10, 0, '1', '{\"method_type\":\"2\",\"name\":\"CoinPayments ( Cryptocurrency )\",\"min\":\"10\",\"max\":\"0\",\"coinpayments_public_key\":\"5a6f3154ddf28c2017df7ad00ce5c1f2b872822beb1ed32f52e0009a2425ecfd\",\"coinpayments_private_key\":\"da16CB5D8Ce6d90eD7181b5907F2103739ef0D5dbF591Ddf22d8f93649170E2F\",\"coinpayments_currency\":\"BTC\",\"merchant_id\":\"db74662404abc41263c87ed221718ce3\",\"ipn_secret\":\"5566\",\"fee\":\"0\",\"currency\":\"USD\"}', 10, '2', ''),
(9, '2checkout', '2checkout', 1, 0, '2', '{\"method_type\":\"1\",\"name\":\"2checkout\",\"min\":\"1\",\"max\":\"0\",\"seller_id\":\"\",\"private_key\":\"\",\"fee\":\"1\",\"currency\":\"USD\"}', 2, '2', ''),
(10, 'Payoneer', 'payoneer', 1, 0, '2', '{\"method_type\":\"2\",\"name\":\"Payoneer\",\"email\":\"fazilakbulut@outlook.com\"}', 1, '2', ''),
(11, 'Mollie', 'mollie', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Mollie\",\"min\":\"1\",\"max\":\"0\",\"live_api_key\":\"\",\"fee\":\"0\",\"currency\":\"USD\"}', 15, '2', ''),
(12, 'PayTM', 'paytm', 10, 100000, '2', '{\"method_type\":\"2\",\"name\":\"PayTM ( INR )( UPI \\/ NET BANKING \\/ DEBIT \\/ CREDIT CARD)\",\"min\":\"10\",\"max\":\"100000\",\"merchant_key\":\"IR6iRT5L0tOxBte4\",\"merchant_mid\":\"gVkWqH50536759745964\",\"merchant_website\":\"DEFAULT\",\"fee\":\"0\",\"currency\":\"\"}', 8, '2', ''),
(13, 'Instamojo', 'instamojo', 0, 0, '1', '{\"method_type\":\"2\",\"name\":\"Instamojo\",\"min\":\"0\",\"max\":\"0\",\"api_key\":\"a2bdf5035c16ad6db389caeb5ceb5273\",\"live_auth_token_key\":\"81ef2affdc5ecfde9b88b13e1cd67cd8\",\"fee\":\"0\",\"currency\":\"INR\"}', 16, '2', ''),
(14, 'Paytm Business', 'paytmqr', 10, 1000000, '2', '{\"method_type\":\"2\",\"name\":\"PayTM QR (5% Bonus From 2000rs)\",\"min\":\"10\",\"max\":\"1000000\",\"merchant_key\":\"https:\\/\\/i.postimg.cc\\/tJ3V6t3R\\/Picsart-23-04-28-13-12-57-778.jpg\",\"merchant_mid\":\"HYJEZD46937702834501\",\"merchant_website\":\"DEFAULT\",\"fee\":\"0\"}', 9, '2', ''),
(15, 'Razorpay', 'razorpay', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Razorpay\",\"min\":\"1\",\"max\":\"0\",\"api_key\":\"0\",\"api_secret_key\":\"0\",\"fee\":\"0\",\"currency\":\"INR\"}', 17, '2', ''),
(16, 'Iyzico', 'iyzico', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Iyzico\",\"min\":\"1\",\"max\":\"0\",\"api_key\":\"0\",\"api_secret_key\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 18, '2', ''),
(17, 'Authorize.net', 'authorize-net', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Authorize.net\",\"min\":\"1\",\"max\":\"0\",\"api_login_id\":\"0\",\"secret_transaction_key\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 19, '2', ''),
(20, 'Ravepay', 'ravepay', 1, 10, '1', '{\"method_type\":\"2\",\"name\":\"Ravepay\",\"min\":\"1\",\"max\":\"10\",\"public_api_key\":\"0\",\"secret_api_key\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 21, '2', ''),
(21, 'Pagseguro', 'pagseguro', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Pagseguro\",\"min\":\"1\",\"max\":\"0\",\"email_id\":\"0\",\"live_production_token\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 22, '2', ''),
(22, 'Cashmaal', 'Cashmaal', 10, 10000, '1', '{\"method_type\":\"2\",\"name\":\"CashMaal (USD)(JAZZCASH)(EASYPAISA)\",\"min\":\"10\",\"max\":\"10000\",\"web_id\":\"5396\",\"fee\":\"0\",\"currency\":\"USD\"}', 11, '2', ''),
(25, 'Refer & earn', 'refer', 0, 0, '1', '{\"method_type\":\"2\",\"name\":\"Do Not Use\",\"min\":\"1\",\"max\":\"10000\",\"merchant_key\":\"P#n%aKfB3&DRAMqH\",\"merchant_mid\":\"DBWvgX98800736620578\",\"merchant_website\":\"DEFAULT\",\"fee\":\"0\",\"currency\":\"\"}', 25, '1', ''),
(26, 'payumoney', 'payumoney', 10, 0, '1', '{\"method_type\":\"2\",\"name\":\"Payumoney\",\"min\":\"10\",\"max\":\"0\",\"merchant_key\":\"B6DBoS\",\"salt_key\":\"fRRSQ28zrxlqM7KmkcPc6ElidMvmr3uw\",\"fee\":\"10\",\"currency\":\"INR\"}', 20, '2', ''),
(30, 'Freebalance', 'Freebalance', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Freebalance\",\"min\":\"1\",\"max\":\"0\",\"merchant_id\":\"\",\"merchant_key\":\"\",\"merchant_salt\":\"\",\"fee\":\"0\"}', 30, '1', ''),
(31, 'Perfect Money', 'perfectmoney', 5, 0, '2', '{\"method_type\":\"2\",\"name\":\"Perfect Money\",\"min\":\"0.10\",\"max\":\"10000\",\"passphrase\":\"6Pz337r9ldFXvwKbLUxZyifbU\",\"usd\":\"U33965619\",\"merchant_website\":\"smmxmonky\",\"fee\":\"1\"}', 7, '2', ''),
(32, 'Coinbase', 'Coinbase', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Coinbase ( Cryptocurrency )\",\"min\":\"1\",\"max\":\"0\",\"api_key\":\"\",\"webhook_api\":\"\",\"fee\":\"0\"}', 23, '2', ''),
(33, 'Webmoney', 'Webmoney', 1, 1, '1', '{\"method_type\":\"2\",\"name\":\"Webmoney\",\"min\":\"1\",\"max\":\"1\",\"wmid\":\"\",\"purse\":\"\",\"fee\":\"0\"}', 24, '2', ''),
(34, 'UnitPay', 'UnityPay', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"UnitPay\",\"min\":\"1\",\"max\":\"0\",\"secret_key\":\"\",\"reg_email\":\"\",\"fee\":\"0\"}', 25, '2', ''),
(35, 'Payeer', 'payeer', 10, 0, '2', '{\"method_type\":\"2\",\"name\":\"Payeer\",\"min\":\"1\",\"max\":\"100000\",\"account\":\"P1059667343\",\"client_secret\":\"tQCaSXyX94pRgpOt\",\"user_id\":\"1654044737\",\"user_pass\":\"tQCaSXyX94pRgpOt\",\"m_shop\":\"1652134607\"}', 4, '2', ''),
(36, '<b>FundsSystem</b>', 'funds', 1, 0, '1', '{}', 26, '2', ''),
(37, 'opay', 'opay', 1, 1000, '2', '{\"method_type\":\"2\",\"is_demo\":\"1\",\"name\":\"opay - Visa - Mastercard - Mobile Wallets\",\"min\":\"1\",\"max\":\"1000\",\"merchant_id\":\"281822041448063\",\"secret_key\":\"OPAYPRV16499350091410.788976381970694\",\"public_key\":\"OPAYPUB16499350091410.6534196662876502\",\"dollar_rate\":\"18.5\"}', 5, '2', ''),
(38, 'Custom', 'custom', 0, 0, '2', '{\"method_type\":\"2\",\"name\":\"\\u0641\\u0648\\u062f\\u0627\\u0641\\u0648\\u0646 \\u0643\\u0627\\u0634\",\"content\":\"<div style=\\\"text-align: center;\\\"><img style=\\\"width: 284px;\\\" src=\\\"data:image\\/png;base64,iVBORw0KGgoAAAANSUhEUgAAARwAAACxCAMAAAAh3\\/JWAAABiVBMVEXwKSL\\/\\/\\/\\/\\/\\/f\\/\\/\\/vr7\\/\\/\\/tKyLwKST\\/\\/vz8\\/f\\/xKSHLTEHzJiDoIxP\\/5+T1JibkhorVOjTuKSfuKx35\\/\\/f9\\/u\\/pLh3\\/8en\\/+f\\/ktazanpjkHSD4\\/vvgioXiHhnpsKvFRkDLS0z0\\/\\/\\/\\/+e7\\/8vL\\/9v\\/6JCboLiLjm5f\\/+PX1KBz2\\/\\/ny\\/\\/PHOTv97eL0Jirt\\/\\/3RISD\\/3N7\\/Ih795NnfOTP42dPfe3XZGh\\/3zsj\\/7evfMyDWTk7zKhjrKiz\\/6+Lsy73dOUDqlJf3t7bQUFbLOzjFUk3sw7jWaWjmlo7o0s3ju6zhs7Xz3uHUSUjVg4LIHx3lqKzlYVfCLh7VIzPriYDOZFrgjnzlXmnfWFHBWlbbZGbDiIzFZmHmopf5ITfZjY\\/0TUnrb2z2v6r57db709\\/UIgzxh4S0SzrGHRDdLD3sqrPQjIbjyrq7Yl61HRbPcHa1LyfeM0n7pbnfdmjhoKT3oZrRd3usKR3ds7LCHSrPcH7XXHfcSz7moo3FLUHKSi+nRjrtd4\\/\\/3u7CBUQYAAAa\\/klEQVR4nO2di2PTVp7vpXOOHqfHVizJihIpMki2FMkmtmLHlmPsBIJJ0kJIhwDTMrBsSzNLS2+Zu9P2Lru9s4+\\/fH\\/HdiBQGjOdTJgm\\/lJDE9uy9PHv\\/B46L0GYaaaZZppppplmmmmmmWaaaaaZZppppplmmumMJcn1gU4plWWZGuxkGZRqjEq6rkcSYx\\/6zM9AVNN1yTAMuGRNAwDw0N714E9RWdKjyJI1WYoo\\/dBnfgaCC6VJP0nY4Nqlm5em6MreMNXDUJKaYRR96DM\\/A+kSbYZydrXUmi+vz09Vvnv9chaxZlOSPvSZn4EkyQgHV7bma40GssWTRYjvE3N+8VpdipoXwedIFnVutF1iV2w0XXYFkWrcHTosuQA+ByJUdnPV9UVkI+KSabJtGymu0i0kxgVoVrSvHWyX1WrVFVXVxe6JIipSXRebtrLsXYRWRZmzM19WXdN0CUL4ZCEwrir8q6KNgv6hz\\/wMRFlagouG1gKWM10+4S\\/11eJuJn\\/oU\\/\\/7i7JCyyWiSkRsTvU4YDembfvIJ9Xt9EOf+VmIXQmIihvuxwvTVVr4ZOHW7YZiVkm+cAGcDu3vBUjFZnxnP8scb4qcLNv\\/NCZm1d4oJB\\/61P\\/+osll8LCiK87l9Lox5cUSlQyvJIomRhfDcpLL5gzOL2gG5wTN4JygGZwTNHPIJ4l9hMWiMg1OkiSGZUW6bnklBV0kOGg6nEiSJYmFYciyBUWdwXlDel2TJVnWwtApIWJidQbntWjSZJIQ6fIYjnsxyof3hGNZCZVkPdRo7xMTfM4MzjFZhpT+7ua+JhvevdUKnsE5Jhom9Zfdle2H+\\/Wwd+n6Kvbz1wAOpee89+r9LEejXqfsYtzdSVmSHVxvtYcygKHnvN\\/z\\/eAw4e4m9l1SDbo7Bx711r4oWIydc7t5bzjOUtFVfZUoMW510kSw+gljTJbP983S9\\/M5+rVuVbF9nygKVBvtTsHhfTNUOOf9nu9nOekiUrFi2yLvnyGumX9yLRvoAj3nvVdT4fDLpx\\/N+wi76vg2u+L6qt2+V8hkZljcfM74lM9OU+AwrSeFg\\/RW7PoEoeMd5+bG8jXHoAIAkjRBC+u6dO788xQ4smwY4aAzr2DyFpyKba4s7mV8UJOmQ2Gqn8PxTNPgSEk\\/vLZRNRWECDkOx\\/d9HK8v3HTCEKzHkM7jYK8pcKgQCVmp6rs\\/gyMS4ioKun3rRspv9zBBohcODuuldwJ11KbehKNgRSFEtVHwyX0v00Mmnb+cZ1q0YvUb81V7hEZ5y3BUYObXFKSUb93f19m5c8eT26SYAJy6lhOMSA8nF6nLIViDpB2sktGQrzfb1BgP\\/I63NyQGm\\/czLTFkQT5XgX0MB5GlHB9xa9F6feI5dI2Bk9XSElZt9+dk3hCq4GK7k0rnrWWN4djug37h9wPZamqDV08ZUU\\/yFovQqKpT4Igkjt24+xmFcuI8VaNjn2Ob93Kf55dS2gRzmTwhWUmYLcU1ZPvKFDZiFasNvz2UOJxzFLPGcBR3Lu2S4POBQVk08RqWFdZ3Ah9ViG+jKXBiXG2sP3Skc2k5rvuHkkpM+O6pZIyvLjJY9mgdYrXqiuo0y0EuqVw\\/nNYp+FsTZZfA5xCX3Ma+rcQLh8wy6lAyGIIUCvefuraNGq7t\\/7LPgUQQKgvbxd+8tPr8iOcoWvHuYBe7k+9fKT5ONWugC\\/wun\\/Mw7\\/vTxm2PBlASgoubQy1nfeirOWW9AYdf5HJat\\/R\\/+qe6kXZWAlv1p8CBEgIyIGS2r+hNeo6MZqQ34CguNK3SgSHXB4Nnc\\/O1hl2ZBkdEUIG6qHtJT\\/rn7p4pZcfguOBiCO7eyPrG3cdlRHwyNUxB8uxXg+6VQZLr6dqHvppT1huW46oQtpFbLt281MU+xCmwiemWg4PSUGcMKo9zZzm5h9hVjhwyqpqYQM4Xl21VVZHCR\\/1PERHjxZeaYdFQ+43fbad8LqIBFRCjo95K2Vl7suGqb9+pmcoDMIo+waap2GjjURaeh6RY1rnPlGSZR2oLqgPn0pfzZkO1lb8KjjgqyHGMSMPF23tOZJ2H7A\\/gaCxJLMuQpIhp2dXHQa3KJ6FNq7rfwYZgfq8ifyflXRDnoWKgjFpRr2dAgSB52V5pXoGARJCN\\/jo4SITX8\\/lZuHQtDKMoDM+FK7agcNLCsO7sX77Xjd3RFBj4Tz2hPHi34Yh2RSl\\/c\\/UwSSIZjjf4bbvikeTBP3\\/R+eKPc9e3VmM+Kw8hsza61qkB+204CFW2bmRJIkGlIUvno8NKj9LfPfjyabGIVRUsBkG8qUL0FpFaQT5ChE\\/jVCAUKSPx+WfKiOGox0qJsQmZUMUmrv3Vkz1PpoYBPkyQzkm3A1xF1Ht2cHXuVj4wXdN1VR7GsQtOmUCtoJLxbEU+C9gniM8+46Dcqg9w\\/EbDV+D3Ls4v7BykxrkAclyUhZqsU8FJ93\\/qLHfb86YrcgwYx7jBgRBV5Z0u+PVkT\\/j\\/OI4hGyRQWhC73Cp1ssNc39POHRxJGC1JYRiWBOEqHV5+cb3UxmA\\/LsEY2SoZzVWExsYVBDiIMe9iUAmfyBcErYWlj\\/ZzTRZle39cOw8B6rikCPwDZYbEM+UkoYLuOIf\\/Eri8sazng6KJx0P9EZ9iPrIi7mzAkOLVbmnp\\/k\\/PwGT61mHhx68q+cK5cMLHxQOLkYxWNJFZyKgUWfrNmNgVhJ98fW3vs87S8uJiqdseqdvt3rp1a3nuj7\\/fu3aQOY7GmGQZ+sPtfGyj\\/PBDX8tpi2pgN5Tx0CtFg4EuU5aEN2zfV6rFJU+wDMb4TMXcWIf8L++wZ1lWDh5Qi4VCpA++IaRqmq2LMNT2Z1OKTho9e9FmzczmW52gGZwTNINzgmZwTtBsGuNJer9pjGNdRDjvMUh7rBmcEzSDc4JmcE7QDM4JumhwaHIJi+YRHHry2qQSVOUXC87rPEcz5JMlaULildBFgsMz5CqZy0lhv67V60cPTasf\\/3H0CDXmfHqh4PA+Bm45tNmXpkiTrGyBXCQ43HIQmrMGdWMaHMYdMrowa1mMLEcRY\\/HOYZpGsv6mwM8c\\/8lxep73qX2RLAcrWFTU0r17c\\/eWfqa5uTd\\/vjf3sX9h4EzynHd1+o56PUU+duftpy8WHEx+RkUZ9+lVG7yPE8\\/gHIPjEsKnmikKqlQqtlI9bjsXJ5S\\/G47rgiMyi0EQmFjlAw5mlnMcDu\\/0FPnoimKt4av2DM4xOIpdedIZ6flq7JMZHFG07YoN5mKDy8Htwz7v8TSyEjgZZKtIESv2RYbj1r59\\/vzOIsIAp5uNez6dBW43tW\\/vPHi+EFxkOGr8f7yc812MXVU8BgfBEy8cz7myfpHhoMpOszn403qM34Zj\\/3vd0P7v7YsMRyk+6jfZszI0K+VNOMU7SZ8OVy4yHBQ8v\\/ts\\/zJSJj6H\\/3FKHE6w+OzZd59fyGZ1VB4gtXw7f3udT6HC3ZSPjbOkbAEDLBzn2\\/n18YhchGqmfSHgUGOPL1D\\/RmmpEt9Hty+vcV27vOkSZL5RPnA4ty8EHLY3\\/\\/b4dQKluBKvj5TPuw31rSlpqumSdnoh4Kx13bdGsI9mQxztO+OCFaE3DQsSQnchuxBwsuUA2eRNOHD1\\/EYFHg1Ihr\\/MN+kgJdhxLgKcRB62YvUtOAoP5mM2\\/F\\/zrXanQiyTz8FckGmi\\/TB7Xn5rpp4CONBodD\\/4ZhG\\/bnb8dURUSPBIO3fzpN8hPmQ7vW66Kl\\/+b8omRZjPlQBcKHiQXYxt4wTL0A+uryvEV217yh5FlQrf\\/Etc6QxCGl0EOHpkMDn7fGseWs\\/k7vE7NE5wFNc1g3zpIycUonMx6XWaZEkyEkPO9jrLy8uLU\\/W4M0ybidW7IHBkHfAYUpRlmTNNguNEkdA0LD5H4EOf+RlI0up1GS5V1phh0F\\/S5MWUMSpEkSSHFwMO3wNWpqOBOXxpbGG0ctLbjyNJo6kRfNmyczehaKaZZppppplmmmmmmWaa6bV+UwtMnPGii5Gu61o4YCyqa\\/\\/oVXOkDXQ9Oru7QjRJmKQPoiQx+EYn\\/9iiTdYMaXhmnydZhrRWGA6j\\/m8ATiRZyZneiWZhtttqtf4YQbP6R3c\\/etbLvDNczVSK6uki9slyGtXr+tl97q\\/S2m6p9MUZ3k+UeqGziAm57hns11rOX3eL729YcH24QciWd4ZrU7Kw3ul+3J7zElYfjM9bjgzDmKxVJ+ksikJNM4Cd8a7TokZUD6XIiLTQ+mWfVdclq8lkWRdone8MaySRwaSIsfc0A0mCyJErbDTcf\\/VyBpyqfhb2Q3M5b\\/\\/ZYbZ\\/eJhrToJkPcvSbDBu25IcWpIGP2fZgCXvOGsj6aVZqoe9SLN++YR13bDCrNdLrb4haDKgLqSDg7X6+0YeOYooMw6+mg\\/+dWDQPtXPxANIf\\/623XrszbW77QdHi6le7eZbrd3xAD9qJImW7vI1p7bSdzQIy0jud7ubjzMjAfv6xY+JaCI5X7Tz+etZFGkys5yFollcuZJF73WWmqZH6dpwOPQOh4W1tUga6GeQ7VBhDlfETw5LuFL53uuPf7fXUgledsZwkn4yuLmCCCnvSO+wnEgKO4ptt1Nq6PVfhmMZTT3txCr5JqOWIDM53RSRO3\\/pPQ1A1jU5\\/aG18tXXn63ebt1LqXwmzUq6U1SVhcPHgSqWvPHF05+eEt\\/cHcMB0xHudk27YT7Oknd8W3q9\\/kLx\\/W5qWb3ByXAGnWLV3cr6fVli9GCTqO78sPkO3u86y0EYpqVadf3K\\/aKPF9NmGL2fyf1Nos6dwAw+TZfn54PHmT42lr2nCJkTy5F13XlQJAS37ybCO75nOWR\\/XgmKX6YUctcTlu4yaKT\\/rrWe\\/yGFjAHy8awr2m5w6T2XRdZ1lmTLmJT\\/8pmtoidZ04hOMSejVJYEpgu69GpPKRrJDHwBOGTPE5zD3GEulHjew4yrAbKVIziDwV6rZquVnV6\\/DvBeV36M8hOkLOntgwMHJylJBv8t79jkVi\\/xGfdHSYkWWeCQs8zJGYYc9Yyms+kSN74iwLuYzJhB2dFWTpIQjnoK+XR+TYbT5h+pG0bv4Y8\\/\\/jjodV68uBolkX6KRYTBIJaGd9cKBXY0hChZK0T7Q1nrNwtX1tYKLJfUC+laYa3Zv1oWsbjscTgUEugS3xzv1v\\/r5eBqI10+so8kGh4c3IU4zjuGdaNvDYfwbs1oRpY8yNL0LrxCmBgbDXu9hGUHB6kHR4l6UtP5VvRJcIUaEMXW1nq8V11K+JHgAXUM8\\/YLmQe1jWFB5aczSdZk79ADvJByQJkz0Pun14FqUJkarLS6+kM2iYLgiiEmtdO6lVvOr7a61yJhsJVfbW9l0TE4gpztxD6p1lZa3e3FG+lAp2ziWeS99urqyhd8z0C5XhfYfnd1tbU1iMJ6mO5sdVuthU5Bax5dQqSnj0oQBTcfX81CyIiyzREcgSWWB7Hwq1vL99Nmk0UWsIPX\\/n65\\/T+r28\\/\\/k2+9Jw\\/0hDGaFZYW2q3W5u7lNGSadop1oCTLCfW+JaSbHsHxvkeNRrxfN9i\\/kUZt5dpAy277vttO5WNwpKjQdlVUQ5WKrYrrW1+H9Gi3Lv1mEV7+xIOWJEPhob3ME7XxcRbRwbVuzScNl5ibNyfWL0Xa11smrhKE4uBxGlq9V3BCw\\/veJqaJ49V\\/T\\/l2BxIFYw0QcavV+Kv\\/GCRNNoB213Tud8suUVUlyP84AFanmOhwOCzjcDI28YHeMvL9+K7RT0rEr7a+TppZi\\/iknSUTODzRlw4fF4mtFE1RbVSLJu5eHRwNe5QBDhHnRnA0o8\\/2877qdx3DGnZNvhZwpVLBrUv6JOk+6FZVv2oDYhx8OWB9ZwyHQl4NcHyCgD1aKIRNsJu1L6uNis1nitqVnYivvA3uDTwf8VW+srIb33GM6BR9DpUjgLMpKttOMjZI6i1XFHv+Lu03FxQFtzmctmgrba\\/\\/Go5s\\/a5MCOLTWvnugbZaa13Rj6LvzUC08RgOuJxkP6\\/YeNsznn2J4VLNWq3mo2BrbRT+qbML1+sG7VaxRlDQ8ZIJHHBqlvN4ZcW2UbVWDEoHGosG1wNSUUyiQkJR7F6RE6gdov2taoPE691W4DYa+auRcYrFOeNwnE3F7Gba+IYIdb5HNVJ+CZa84Cu4dS1iGbQg8bjlgAP+qfOgs8PnJi4txKqv2vEnz5rjQ0Y3Y2TjJQ6HR1r63QZW8HYaDeeJqswvP7y34kImcyMZfTXDlkL8\\/I00vb+hqmp338i2gTbAsSBOpPs\\/PdxtY9euxM+zENqnWVGLy\\/eXVhFRwUqaEpz7ozKqKN2baboUu6q96DUHJ1ztXykq6Ix6myJvVhGPjZR615FP8L5ksAXwBq0DgUKzwuSrtP9TGXzAogfR2KJJLtfv5\\/rM87KHLTj9avH+JBU0bsZExHc8aukhRHG6nxdVtL2fdETk4ydO3+vEto+XIIazsHe\\/bCP0xDOgDYEFBlfgixKJCnDAxVBdCwUn\\/f9F366t\\/yUUbuAGVj49zHlXNxpEKXl9aEPeLkZi8FnKmvttF0Hbb56iQ34Nx0uk13DEeL8XOf+Gkb9R6EVZCynkqwOAgzBeFkLGtzobL4MTsiQcXM67th0\\/zo7gYKLgOYGN4CQABxGxmya7RBXjG\\/WcNdwgvlvKNKled16Ivhr\\/ixay+o8Yu8FlCkngCA7lGzhCDRJq6acVVFP+m+WgyjCVFzlDSrtiBcEJGz0hKxEV3V7TjcT5RkRk4yD8O8AR4bPkCZxlCELlNEmcW6Kqrq7lWLaKVP+rNAE4MfreCUMaWVQbSbYs8FmdInjE1mTNZ2kCJzGgcKdjOGCYuR98Fc1fFvpJ1oI8r5uF8kBLOj44oP\\/UB8LgRRGT4GGUHsHhR4p6uYTqe2VSU77xch2lgs3\\/YE0t7RLfb2eC0aNOyeRwNMuQvyf8qzzNm5YTOEjsZq\\/hKDW1\\/J0V7bdx1e9mfWPYQiouZeyjMsGou8\\/z5aNFpwTLykHL2cR2o3h1DMe6GatjOFoYgc95CXCgdDKWoLEVnw+AZdu0xW2e6if9R1hFyn0rMbInJiLxpVdwICelIbRdK5L3W1VT6R7m\\/myqZfP7jEnpNga6qRxCQr1bxHh+DXLJbAtcWbtwmn0Qx33OEZySCGfxX4VCZz6uuVuQ3u4GBMVLjrC37tfseGnvGmjtuF6WMGkEnXEuAD5HVPATj43hSN\\/Ni6q\\/5eV+HyO3trIz3PtLC9tit7BWGK6lj8oxtm9lTe\\/laoOgdsGYwKHSWuHa13DoQmHtZdfF4seHSSHw41r5xbXhlS42cftPQziLK8+LMTZ3s7q3t9IgGDLV0wzlAEcAOGClxhGcbRGrytOVfNyoKA0+3y6u+ij\\/EZMKq6Rqu2awPj+\\/srEy0noe\\/iefL6tEib\\/PjQ95GVyTuXxoWNCsINEdBoTD6XuQEPhKJb+aN23ixysrQTn\\/NF\\/BNRtt\\/Xhny23Y6FOneTiGw37qPg3W8ysbwUZrxfUVtHHY9BaQWbPL5WDDJHa11lpZj\\/Or676NSPDpi6VW7LtxR++9Xzn\\/XoLyTQqdb93G\\/Gc8bQAvYhRaDTB1jBCCz1VsOFfV9\\/Fi1hTS0RUgPi4fjRae58swiArfXNJW4wkcyoZ54prdfZ0BHZo4L7Cv4gfMiHbWVbuC\\/Jhve+WjCj8SRF\\/XtLGIFPBL9uplqZltYkLKV4RCG5oy37sbgWnBk+1nzdzN+YZfQUiJFdVWSQwJJVaIa\\/M5XLFZU323+5Ke5h4SEtTFUAkrDfNTJ+HjqyOjU4aLMd3X8l0Xb6+FiaXv5d2Gz3e54Gv0H1O1ivwGXpxYTrpdVVHw+aBp9ephuA8OAgUfNYWe8MT0\\/Qak35DkwkVX+HI6Rx\\/BF4+Zf+hAbrOpIL98SShs+KhmTj6lQiCTaCbZzjqpuvCNjJZWqcKbJqdJ+NYAKlq9PIAq41ThWE2vS4q48sJjkJGvXdqIK6oZBK8nKyC0AWUPkwTD+6wbV0frvohvzG3AkGzgIziWvhPYFaX1J7lJI+3wQYCVgGdREXt2v7tSc1UClmny5T\\/gMK82W4nz259nYV9It23kFy8lhXzFhvg1fj6G+uRlxLTB1a2VIt8vLIaWWzQJOTpDOES8\\/v0Qwt9pdtBQSZMSYdfEFXv9zj7UmDt5V1XN7p3nx1aT2rma1aWeFOq9Xnpj7s7S0vWfrzm1tHTvi3G0MmjaxZBGdi9nTvan3afYrwY7GpSYkDFnH3Xm\\/vsPbgOhj58\\/X378+kOWOnuZzpp9Kd3d3t5cWGPpvbmlB6\\/Wtnr+vJMaht6LvKt35p784TZvZ3fmru8enSI8doapzBLjNDerZpEmGPLdru3XipX89kK7TFS7+nQ4SHOvlCRNaCGRoA3qMuTNhsEX7TByP9OktYdS9NkK+CYSd0tb+QA8jruQhpHOpHoo99K9R9sBsSs\\/9hkE6mTyTs2B9txPEioPMkiBvVCPcjnPaE4+hcmOEDYT2cgZ+mD4ealMGspiFrKjT\\/Y8L9dvNg1gI5xitEqiumAwZ7harSqkAQJzxxv3JVa3jonKEvjWnhaGksV3Q3uXDGty91aLqLdUrthQCPpVF0ontFUYGJLG3980PivWitUGzl9JEvBxk2NBKiwZ\\/X4EObrE4EhSU+tZfStqHh2bShIU\\/cAnirKnxSoU6+ufR4kVGZP3wx\\/+MkHX6SlGqzEcPRt2K3ZNgTikBMWVR+CbmfZKo0XsNMaMvgXVjiFr71R41GmsQzmY\\/pjHvB6F2FKtbh9AIg0G1QOrk66WwR27Kw8H9TpfEW\\/8Xt7HIgAiXZesPnwDEWN62NQGYXT0vKzzhSkjOYye\\/U+Fh8a5DEgN6q8+vl4f6IKm68IpwhmL0kFhblXBfFPb+dIlh0nSr6\\/8JUieosOfttahgoKkuPVgn41NnWoy4yW7iLoPnV9j\\/fxGbvRsXcFBu5Od2XQS1mxqWeHh7g8\\/XO98tD\\/g392v92ujbcbB\\/K91rj9+vHvVCY+6g6mmC8ZPy4tLNw6yX7XpIlQUTOr98Pj5w+yEfsLTlmQZCRMkz8scmbFR0\\/71dxv5BvXgpKzIqTPmQfSgk13Led9DEh04LAzZCd3nvyjKyy2ZNzlHP8Nt3vWBLhnw2dJo0yoKvlX+m5oV36InCcNwtNGTpB9tsCgBnKRO+d3g5q9oVnCCQqhJjO86dobjTTRwbPCZfMcqaNWgU5ggBoFH4t3fcl076g4GTAYwY1HvVxkm7\\/liEDdlPYr+tj0b\\/xdPGuULnuu0twAAAABJRU5ErkJggg==\\\" data-filename=\\\"download.png\\\"><br><\\/div><div style=\\\"text-align: center;\\\"><b><br><\\/b><div><b>\\u0644\\u0644\\u0634\\u062d\\u0646 \\u0641\\u0648\\u062f\\u0627\\u0641\\u0648\\u0646 \\u0643\\u0627\\u0634 \\u062a\\u0648\\u0627\\u0635\\u0644 \\u0645\\u0639 \\u0627\\u0644\\u062f\\u0639\\u0645\\u00a0<\\/b><\\/div><div><b>\\u0631\\u0642\\u0645 \\u0627\\u0644\\u062f\\u0639\\u0645 01125319977<\\/b><\\/div><div><b>\\u0627\\u0631\\u0633\\u0644 \\u0627\\u0644\\u0627\\u0645\\u0648\\u0627\\u0644 \\u0648\\u0627\\u0631\\u0633\\u0644 \\u0633\\u0643\\u0631\\u064a\\u0646 \\u0628\\u0644 \\u0645\\u0628\\u0644\\u063a<\\/b><\\/div><\\/div>\"}', 3, '2', ''),
(987, 'Gbprimepay', 'gbprimepay', 10, 10000, '1', '{\"method_type\":\"2\",\"name\":\"Gbprimepay\",\"min\":\"10\",\"max\":\"10000\",\"token\":\"nfu9igxPo8AiVpD4oOEs/3i+aoHTIpld+zegPTJZKXLS9QJH60zzUQk/2BuQiRwLDb9d8r+MvCNKD34KjIq37WwtAAHDSFZlDXkbJaT3h2ws94EoUYVNNfLK0I+Lh0zfDi6pq1O8FCZi+wmCrW7OBuuYLWY=\"}', 1198, '2', '');

-- --------------------------------------------------------

--
-- Table structure for table `payment_methodsold`
--

CREATE TABLE `payment_methodsold` (
  `id` int(11) NOT NULL,
  `method_name` varchar(225) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `method_get` varchar(225) NOT NULL,
  `method_min` double NOT NULL,
  `method_max` double NOT NULL,
  `method_type` enum('1','2') NOT NULL DEFAULT '2' COMMENT '2 -> ON, 1 -> OFF	',
  `method_extras` text NOT NULL,
  `method_line` double NOT NULL,
  `nouse` enum('1','2') NOT NULL DEFAULT '2'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `payment_methodsold`
--

INSERT INTO `payment_methodsold` (`id`, `method_name`, `method_get`, `method_min`, `method_max`, `method_type`, `method_extras`, `method_line`, `nouse`) VALUES
(1, 'Paypal', 'paypal', 10, 10000, '2', '{\"method_type\":\"2\",\"name\":\"Paypal ( USD ) ( International Payments ) [ 10% Charge ]\",\"min\":\"10\",\"max\":\"10000\",\"client_id\":\"AWWRCH4eG0dDMY_84cDXJVKVsBGSzJpnezbgAB4Qm49cTQ2dJwZWMaWzNAbUv4ojUunW-pgicoYTMA0l\",\"client_secret\":\"EMiHDg3EejaX_ns8h3ybEkgBcm_mbFfPoK_EeNyW_UGX_LJlKxa3lpW9nDf7-gRrQMV1kyUWS1J48NxC\",\"fee\":\"10\"}', 3, '2'),
(2, 'Stripe', 'stripe', 1, 100, '1', '{\"method_type\":\"2\",\"name\":\"Stripe\",\"min\":\"1\",\"max\":\"100\",\"stripe_publishable_key\":\"pk_live_51HiUnRLjkQAtcIW0F983imoO8qhftSSMSj7oB9xTjGHB51su6vnuDmGNs5l2NNZz1XE1Ogf1svxqjtdasRYr3atk00wEAHHKNT\",\"stripe_secret_key\":\"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\",\"stripe_webhooks_secret\":\"whsec_gSvhMz0eOIOTk5S9uzzzDgpHeclOmiDe\",\"fee\":\"10\",\"currency\":\"USD\"}', 4, '2'),
(3, 'Shopier', 'shopier', 5, 0, '1', '{\"method_type\":\"1\",\"name\":\"Kredi \\/ Banka Kart\\u0131 ile \\u00d6de\",\"min\":\"5\",\"max\":\"0\",\"apiKey\":\"\",\"apiSecret\":\"\",\"website_index\":\"1\",\"processing_fee\":\"1\",\"fee\":\"10\",\"currency\":\"USD\"}', 5, '2'),
(5, 'Paywant', 'paywant', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Paywant\",\"min\":\"1\",\"max\":\"0\",\"apiKey\":\"\",\"apiSecret\":\"\",\"fee\":\"0\",\"currency\":\"USD\",\"commissionType\":\"2\",\"payment_type\":[\"1\",\"2\",\"3\"]}', 6, '2'),
(7, 'PayTR', 'paytr', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Paytr\",\"min\":\"1\",\"max\":\"0\",\"merchant_id\":\"\",\"merchant_key\":\"\",\"merchant_salt\":\"\",\"fee\":\"0\",\"currency\":\"USD\"}', 7, '2'),
(8, 'Coinpayments', 'coinpayments', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Coinpayments\",\"min\":\"1\",\"max\":\"0\",\"coinpayments_public_key\":\"\",\"coinpayments_private_key\":\"\",\"coinpayments_currency\":\"LTCT\",\"merchant_id\":\"\",\"ipn_secret\":\"\",\"fee\":\"0\",\"currency\":\"USD\"}', 8, '2'),
(9, '2checkout', '2checkout', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"2checkout\",\"min\":\"1\",\"max\":\"0\",\"seller_id\":\"\",\"private_key\":\"\",\"fee\":\"1\",\"currency\":\"USD\"}', 9, '2'),
(10, 'Payoneer', 'payoneer', 1, 0, '1', '{\"method_type\":\"2\",\"name\":\"Payoneer\",\"email\":\"fazilakbulut@outlook.com\"}', 10, '2'),
(11, 'Mollie', 'mollie', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Mollie\",\"min\":\"1\",\"max\":\"0\",\"live_api_key\":\"\",\"fee\":\"0\",\"currency\":\"USD\"}', 11, '2'),
(12, 'PayTM', 'paytm', 10, 100000, '2', '{\"method_type\":\"2\",\"name\":\"PayTM ( INR )( UPI \\/ NET BANKING \\/ DEBIT \\/ CREDIT CARD)\",\"min\":\"10\",\"max\":\"100000\",\"merchant_key\":\"IR6iRT5L0tOxBte4\",\"merchant_mid\":\"gVkWqH50536759745964\",\"merchant_website\":\"DEFAULT\",\"fee\":\"0\",\"currency\":\"\"}', 2, '2'),
(13, 'Instamojo', 'instamojo', 0, 0, '1', '{\"method_type\":\"2\",\"name\":\"Instamojo\",\"min\":\"0\",\"max\":\"0\",\"api_key\":\"a2bdf5035c16ad6db389caeb5ceb5273\",\"live_auth_token_key\":\"81ef2affdc5ecfde9b88b13e1cd67cd8\",\"fee\":\"0\",\"currency\":\"INR\"}', 12, '2'),
(14, 'Paytm Business', 'paytmqr', 10, 1000000, '2', '{\"method_type\":\"2\",\"name\":\"PayTM QR (5% Bonus From 2000rs)\",\"min\":\"10\",\"max\":\"1000000\",\"merchant_key\":\"https:\\/\\/i.imgur.com\\/mlAI1qX.png\",\"merchant_mid\":\"HYJEZD46937702834501\",\"merchant_website\":\"DEFAULT\",\"fee\":\"0\"}', 1, '2'),
(15, 'Razorpay', 'razorpay', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Razorpay\",\"min\":\"1\",\"max\":\"0\",\"api_key\":\"0\",\"api_secret_key\":\"0\",\"fee\":\"0\",\"currency\":\"INR\"}', 13, '2'),
(16, 'Iyzico', 'iyzico', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Iyzico\",\"min\":\"1\",\"max\":\"0\",\"api_key\":\"0\",\"api_secret_key\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 14, '2'),
(17, 'Authorize.net', 'authorize-net', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Authorize.net\",\"min\":\"1\",\"max\":\"0\",\"api_login_id\":\"0\",\"secret_transaction_key\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 15, '2'),
(20, 'Ravepay', 'ravepay', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Ravepay\",\"min\":\"1\",\"max\":\"0\",\"public_api_key\":\"0\",\"secret_api_key\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 17, '2'),
(21, 'Pagseguro', 'pagseguro', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Pagseguro\",\"min\":\"1\",\"max\":\"0\",\"email_id\":\"0\",\"live_production_token\":\"0\",\"fee\":\"0\",\"currency\":\"USD\"}', 18, '2'),
(22, 'Cashmaal', 'Cashmaal', 1, 10000, '2', '{\"method_type\":\"2\",\"name\":\"CashMaal (USD)(JAZZCASH)(EASYPAISA)\",\"min\":\"1\",\"max\":\"10000\",\"web_id\":\"5396\",\"fee\":\"0\",\"currency\":\"USD\"}', 19, '2'),
(25, 'Refer & earn', 'refer', 0, 0, '1', '{\"method_type\":\"2\",\"name\":\"Do Not Use\",\"min\":\"1\",\"max\":\"10000\",\"merchant_key\":\"P#n%aKfB3&DRAMqH\",\"merchant_mid\":\"DBWvgX98800736620578\",\"merchant_website\":\"DEFAULT\",\"fee\":\"0\",\"currency\":\"\"}', 25, '1'),
(26, 'payumoney', 'payumoney', 10, 0, '1', '{\"method_type\":\"2\",\"name\":\"Payumoney\",\"min\":\"10\",\"max\":\"0\",\"merchant_key\":\"Mv4ctvrc\",\"salt_key\":\"pWUvDRU8CT\",\"fee\":\"10\",\"currency\":\"INR\"}', 16, '2'),
(30, 'Freebalance', 'Freebalance', 1, 0, '1', '{\"method_type\":\"1\",\"name\":\"Freebalance\",\"min\":\"1\",\"max\":\"0\",\"merchant_id\":\"\",\"merchant_key\":\"\",\"merchant_salt\":\"\",\"fee\":\"0\"}', 30, '1');

-- --------------------------------------------------------

--
-- Table structure for table `referral`
--

CREATE TABLE `referral` (
  `referral_id` int(11) NOT NULL,
  `referral_client_id` int(11) NOT NULL,
  `referral_clicks` double NOT NULL DEFAULT 0,
  `referral_sign_up` double NOT NULL DEFAULT 0,
  `referral_totalFunds_byReffered` double NOT NULL DEFAULT 0,
  `referral_earned_commision` double DEFAULT 0,
  `referral_requested_commision` varchar(225) DEFAULT '0',
  `referral_total_commision` double DEFAULT 0,
  `referral_status` enum('1','2') NOT NULL DEFAULT '1',
  `referral_code` text NOT NULL,
  `referral_rejected_commision` double NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `referral`
--

INSERT INTO `referral` (`referral_id`, `referral_client_id`, `referral_clicks`, `referral_sign_up`, `referral_totalFunds_byReffered`, `referral_earned_commision`, `referral_requested_commision`, `referral_total_commision`, `referral_status`, `referral_code`, `referral_rejected_commision`) VALUES
(1, 1, 0, 0, 0, 0, '0', 0, '1', 'dc749b', 0),
(2, 2, 0, 0, 0, 0, '0', 0, '1', '5a80a3', 0),
(3, 3, 0, 0, 0, 0, '0', 0, '1', '192c2e', 0),
(4, 4, 0, 0, 0, 0, '0', 0, '1', 'd7eeeb', 0),
(5, 5, 0, 0, 0, 0, '0', 0, '1', 'cd2cce', 0),
(6, 6, 0, 0, 0, 0, '0', 0, '1', '90ae05', 0),
(7, 7, 0, 0, 0, 0, '0', 0, '1', 'fbca1d', 0),
(8, 8, 0, 0, 0, 0, '0', 0, '1', '58963a', 0),
(9, 9, 0, 0, 0, 0, '0', 0, '1', '323577', 0),
(10, 10, 0, 0, 0, 0, '0', 0, '1', '4bd0f4', 0),
(11, 11, 0, 0, 0, 0, '0', 0, '1', 'c77dcf', 0),
(12, 12, 0, 0, 0, 0, '0', 0, '1', 'af57ed', 0),
(13, 13, 0, 0, 0, 0, '0', 0, '1', '6e0836', 0),
(14, 14, 0, 0, 0, 0, '0', 0, '1', '7a0e8e', 0),
(15, 15, 0, 0, 0, 0, '0', 0, '1', '6707bf', 0),
(16, 16, 0, 0, 0, 0, '0', 0, '1', 'ae4335', 0),
(17, 17, 0, 0, 0, 0, '0', 0, '1', '13f820', 0),
(18, 18, 0, 0, 0, 0, '0', 0, '1', '836149', 0),
(19, 19, 0, 0, 0, 0, '0', 0, '1', 'ac98dd', 0),
(20, 20, 0, 0, 0, 0, '0', 0, '1', '8eb9ed', 0),
(21, 21, 0, 0, 0, 0, '0', 0, '1', '3b3d00', 0),
(22, 22, 0, 0, 0, 0, '0', 0, '1', '4073ff', 0),
(23, 23, 0, 0, 0, 0, '0', 0, '1', 'e7beae', 0),
(24, 24, 0, 0, 0, 0, '0', 0, '1', '124544', 0),
(25, 25, 0, 0, 0, 0, '0', 0, '1', 'bd77a5', 0),
(26, 26, 0, 0, 0, 0, '0', 0, '1', 'ab3548', 0),
(27, 27, 0, 0, 0, 0, '0', 0, '1', 'af125f', 0),
(28, 28, 0, 0, 0, 0, '0', 0, '1', '87d4fe', 0),
(29, 29, 0, 0, 0, 0, '0', 0, '1', 'f6ce2a', 0),
(30, 30, 0, 0, 0, 0, '0', 0, '1', 'b882fb', 0),
(31, 31, 0, 0, 0, 0, '0', 0, '1', '9e7bab', 0),
(32, 32, 0, 0, 0, 0, '0', 0, '1', 'b3f87e', 0),
(33, 33, 0, 0, 0, 0, '0', 0, '1', '955e27', 0),
(34, 34, 0, 0, 0, 0, '0', 0, '1', 'e873e3', 0),
(35, 35, 0, 0, 0, 0, '0', 0, '1', 'd533d2', 0),
(36, 36, 0, 0, 0, 0, '0', 0, '1', '4d94e4', 0),
(37, 37, 0, 0, 0, 0, '0', 0, '1', '4bd044', 0),
(38, 38, 0, 0, 0, 0, '0', 0, '1', 'b6a67b', 0),
(39, 39, 0, 0, 0, 0, '0', 0, '1', '9f020b', 0),
(40, 40, 0, 0, 0, 0, '0', 0, '1', 'b75865', 0),
(41, 41, 0, 0, 0, 0, '0', 0, '1', '47c31a', 0),
(42, 42, 0, 0, 0, 0, '0', 0, '1', 'be2cb1', 0),
(43, 43, 0, 0, 0, 0, '0', 0, '1', '45a1fd', 0),
(44, 44, 0, 0, 0, 0, '0', 0, '1', '3e9cba', 0),
(45, 45, 0, 0, 0, 0, '0', 0, '1', 'a02a4c', 0),
(46, 46, 0, 0, 0, 0, '0', 0, '1', '7a0f80', 0),
(47, 47, 0, 0, 0, 0, '0', 0, '1', 'e20cf2', 0),
(48, 48, 0, 0, 0, 0, '0', 0, '1', 'cd0a35', 0),
(49, 49, 0, 0, 0, 0, '0', 0, '1', '5a581f', 0),
(50, 50, 0, 0, 0, 0, '0', 0, '1', '939634', 0),
(51, 51, 0, 0, 0, 0, '0', 0, '1', '8c3fb4', 0),
(52, 52, 0, 0, 0, 0, '0', 0, '1', 'c68104', 0),
(53, 53, 0, 0, 0, 0, '0', 0, '1', '984089', 0),
(54, 54, 0, 0, 0, 0, '0', 0, '1', 'fa0f2f', 0),
(55, 55, 0, 0, 0, 0, '0', 0, '1', '3abd3d', 0),
(56, 56, 0, 0, 0, 0, '0', 0, '1', 'ffda07', 0),
(57, 57, 0, 0, 0, 0, '0', 0, '1', '98a1da', 0),
(58, 58, 0, 0, 0, 0, '0', 0, '1', '32dc7b', 0),
(59, 59, 0, 0, 0, 0, '0', 0, '1', '84a8b5', 0),
(60, 60, 0, 0, 0, 0, '0', 0, '1', 'b2012d', 0),
(61, 61, 0, 0, 0, 0, '0', 0, '1', '72cf46', 0),
(62, 62, 0, 0, 0, 0, '0', 0, '1', '6a443f', 0),
(63, 63, 0, 0, 0, 0, '0', 0, '1', 'db15d4', 0),
(64, 64, 0, 0, 0, 0, '0', 0, '1', '88f86a', 0),
(65, 65, 0, 0, 0, 0, '0', 0, '1', 'ad2f78', 0),
(66, 66, 0, 0, 0, 0, '0', 0, '1', 'c46841', 0),
(67, 67, 0, 0, 0, 0, '0', 0, '1', 'fc7365', 0),
(68, 68, 0, 0, 0, 0, '0', 0, '1', '6adb64', 0);

-- --------------------------------------------------------

--
-- Table structure for table `referral_payouts`
--

CREATE TABLE `referral_payouts` (
  `r_p_id` int(11) NOT NULL,
  `r_p_code` text NOT NULL,
  `r_p_status` enum('1','2','3','4','0') NOT NULL DEFAULT '0',
  `r_p_amount_requested` double NOT NULL,
  `r_p_requested_at` datetime NOT NULL,
  `r_p_updated_at` datetime NOT NULL,
  `client_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `refill_status`
--

CREATE TABLE `refill_status` (
  `id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `order_id` int(11) NOT NULL,
  `refill_apiid` int(11) DEFAULT NULL,
  `order_url` text NOT NULL,
  `creation_date` datetime DEFAULT NULL,
  `ending_date` date DEFAULT NULL,
  `service_name` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL,
  `refill_status` enum('Pending','Refilling','Completed','Rejected','Error') DEFAULT 'Pending',
  `order_apiid` int(11) DEFAULT 0,
  `refill_response` text DEFAULT NULL,
  `refill_where` enum('site','api') DEFAULT 'site'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `serviceapi_alert`
--

CREATE TABLE `serviceapi_alert` (
  `id` int(11) NOT NULL,
  `service_id` int(11) NOT NULL,
  `serviceapi_alert` text NOT NULL,
  `servicealert_extra` text NOT NULL,
  `servicealert_date` datetime NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `services`
--

CREATE TABLE `services` (
  `service_id` int(11) NOT NULL,
  `service_api` int(11) NOT NULL DEFAULT 0,
  `api_service` int(11) NOT NULL DEFAULT 0,
  `api_servicetype` enum('1','2') NOT NULL DEFAULT '2',
  `api_detail` text NOT NULL,
  `category_id` int(11) NOT NULL,
  `service_line` double NOT NULL,
  `service_type` enum('1','2') NOT NULL DEFAULT '2',
  `service_package` enum('1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17') NOT NULL,
  `service_name` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `service_description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL,
  `service_price` varchar(225) NOT NULL,
  `service_min` double NOT NULL,
  `service_max` double NOT NULL,
  `service_dripfeed` enum('1','2') NOT NULL DEFAULT '1',
  `service_autotime` double NOT NULL DEFAULT 0,
  `service_autopost` double NOT NULL DEFAULT 0,
  `service_speed` enum('1','2','3','4') NOT NULL,
  `want_username` enum('1','2') NOT NULL DEFAULT '1',
  `service_secret` enum('1','2') NOT NULL DEFAULT '2',
  `price_type` enum('normal','percent','amount') NOT NULL DEFAULT 'normal',
  `price_cal` text DEFAULT NULL,
  `instagram_second` enum('1','2') NOT NULL DEFAULT '2',
  `start_count` enum('none','instagram_follower','instagram_photo','') NOT NULL,
  `instagram_private` enum('1','2') NOT NULL,
  `name_lang` varchar(225) DEFAULT 'en',
  `description_lang` text DEFAULT NULL,
  `time_lang` varchar(225) NOT NULL DEFAULT 'Not enough data',
  `time` varchar(225) NOT NULL DEFAULT 'Not enough data',
  `cancelbutton` enum('1','2') NOT NULL DEFAULT '2' COMMENT '1 -> ON, 2 -> OFF',
  `show_refill` enum('true','false') NOT NULL DEFAULT 'false',
  `service_profit` varchar(225) NOT NULL,
  `refill_days` varchar(225) NOT NULL DEFAULT '30',
  `refill_hours` varchar(225) NOT NULL DEFAULT '24',
  `avg_days` int(11) NOT NULL,
  `avg_hours` int(11) NOT NULL,
  `avg_minutes` int(11) NOT NULL,
  `avg_many` int(11) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `service_api`
--

CREATE TABLE `service_api` (
  `id` int(11) NOT NULL,
  `api_name` varchar(225) NOT NULL,
  `api_url` text NOT NULL,
  `api_key` varchar(225) NOT NULL,
  `api_type` int(11) NOT NULL,
  `api_limit` double NOT NULL DEFAULT 0,
  `currency` enum('INR','USD') DEFAULT NULL,
  `api_alert` enum('1','2') NOT NULL DEFAULT '2' COMMENT '2 -> Gönder, 1 -> Gönderildi',
  `status` enum('1','2') NOT NULL DEFAULT '2'
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `settings`
--

CREATE TABLE `settings` (
  `id` int(11) NOT NULL,
  `site_seo` text NOT NULL,
  `site_title` text DEFAULT NULL,
  `site_description` text DEFAULT NULL,
  `site_keywords` text DEFAULT NULL,
  `site_logo` text DEFAULT NULL,
  `site_name` text DEFAULT NULL,
  `site_currency` varchar(2555) NOT NULL DEFAULT 'try',
  `favicon` text DEFAULT NULL,
  `site_language` varchar(225) NOT NULL DEFAULT 'tr',
  `site_theme` text NOT NULL,
  `site_theme_alt` text DEFAULT NULL,
  `recaptcha` enum('1','2') NOT NULL DEFAULT '1',
  `recaptcha_key` text DEFAULT NULL,
  `recaptcha_secret` text DEFAULT NULL,
  `custom_header` text DEFAULT NULL,
  `custom_footer` text DEFAULT NULL,
  `ticket_system` enum('1','2') NOT NULL DEFAULT '2',
  `register_page` enum('1','2') NOT NULL DEFAULT '2',
  `service_speed` enum('1','2') NOT NULL,
  `service_list` enum('1','2') NOT NULL,
  `dolar_charge` double NOT NULL,
  `euro_charge` double NOT NULL,
  `smtp_user` text NOT NULL,
  `smtp_pass` text NOT NULL,
  `smtp_server` text NOT NULL,
  `smtp_port` varchar(225) NOT NULL,
  `smtp_protocol` enum('0','ssl','tls') NOT NULL,
  `alert_type` enum('1','2','3') NOT NULL,
  `alert_apimail` enum('1','2') NOT NULL,
  `alert_newmanuelservice` enum('1','2') NOT NULL,
  `alert_newticket` enum('1','2') NOT NULL,
  `alert_apibalance` enum('1','2') NOT NULL,
  `alert_serviceapialert` enum('1','2') NOT NULL,
  `sms_provider` varchar(225) NOT NULL,
  `sms_title` varchar(225) NOT NULL,
  `sms_user` varchar(225) NOT NULL,
  `sms_pass` varchar(225) NOT NULL,
  `sms_validate` enum('0','1') NOT NULL DEFAULT '0' COMMENT '1 -> OK, 0 -> NO',
  `admin_mail` varchar(225) NOT NULL,
  `admin_telephone` varchar(225) NOT NULL,
  `resetpass_page` enum('1','2') NOT NULL,
  `resetpass_sms` enum('1','2') NOT NULL,
  `resetpass_email` enum('1','2') NOT NULL,
  `site_maintenance` enum('1','2') NOT NULL DEFAULT '2',
  `servis_siralama` varchar(255) NOT NULL,
  `bronz_statu` int(11) NOT NULL,
  `silver_statu` int(11) NOT NULL,
  `gold_statu` int(11) NOT NULL,
  `bayi_statu` int(11) NOT NULL,
  `ns1` varchar(191) DEFAULT NULL,
  `ns2` varchar(191) DEFAULT NULL,
  `childpanel_price` double DEFAULT NULL,
  `snow_effect` enum('1','2') NOT NULL DEFAULT '2',
  `snow_colour` text NOT NULL,
  `promotion` enum('1','2') DEFAULT '2',
  `referral_commision` double NOT NULL,
  `referral_payout` double NOT NULL,
  `referral_status` enum('1','2') NOT NULL DEFAULT '1',
  `childpanel_selling` enum('1','2') NOT NULL DEFAULT '1',
  `tickets_per_user` double NOT NULL DEFAULT 5,
  `name_fileds` enum('1','2') NOT NULL DEFAULT '1' COMMENT '1 -> ON, 2 -> NO',
  `skype_feilds` enum('1','2') NOT NULL DEFAULT '1' COMMENT '1 -> ON, 2 -> NO',
  `csymbol` text NOT NULL,
  `inr_symbol` text NOT NULL,
  `inr_value` double NOT NULL DEFAULT 0,
  `usd_symbol` text NOT NULL,
  `inr_convert` double NOT NULL DEFAULT 0,
  `otp_login` enum('1','2','0') NOT NULL DEFAULT '0',
  `auto_deactivate_payment` enum('1','2') NOT NULL DEFAULT '1',
  `service_avg_time` enum('1','0') NOT NULL DEFAULT '0',
  `alert_orderfail` enum('1','2') NOT NULL DEFAULT '2',
  `alert_welcomemail` enum('1','2') NOT NULL DEFAULT '2',
  `freebalance` enum('1','2') NOT NULL DEFAULT '1',
  `freeamount` double DEFAULT 0,
  `alert_newmessage` enum('1','2') NOT NULL DEFAULT '1',
  `email_confirmation` enum('1','2') NOT NULL DEFAULT '2',
  `resend_max` int(11) NOT NULL,
  `orders` int(255) NOT NULL,
  `orders_id` int(11) NOT NULL,
  `status` varchar(255) NOT NULL DEFAULT '1',
  `fundstransfer_fees` varchar(10) NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `settings`
--

INSERT INTO `settings` (`id`, `site_seo`, `site_title`, `site_description`, `site_keywords`, `site_logo`, `site_name`, `site_currency`, `favicon`, `site_language`, `site_theme`, `site_theme_alt`, `recaptcha`, `recaptcha_key`, `recaptcha_secret`, `custom_header`, `custom_footer`, `ticket_system`, `register_page`, `service_speed`, `service_list`, `dolar_charge`, `euro_charge`, `smtp_user`, `smtp_pass`, `smtp_server`, `smtp_port`, `smtp_protocol`, `alert_type`, `alert_apimail`, `alert_newmanuelservice`, `alert_newticket`, `alert_apibalance`, `alert_serviceapialert`, `sms_provider`, `sms_title`, `sms_user`, `sms_pass`, `sms_validate`, `admin_mail`, `admin_telephone`, `resetpass_page`, `resetpass_sms`, `resetpass_email`, `site_maintenance`, `servis_siralama`, `bronz_statu`, `silver_statu`, `gold_statu`, `bayi_statu`, `ns1`, `ns2`, `childpanel_price`, `snow_effect`, `snow_colour`, `promotion`, `referral_commision`, `referral_payout`, `referral_status`, `childpanel_selling`, `tickets_per_user`, `name_fileds`, `skype_feilds`, `csymbol`, `inr_symbol`, `inr_value`, `usd_symbol`, `inr_convert`, `otp_login`, `auto_deactivate_payment`, `service_avg_time`, `alert_orderfail`, `alert_welcomemail`, `freebalance`, `freeamount`, `alert_newmessage`, `email_confirmation`, `resend_max`, `orders`, `orders_id`, `status`, `fundstransfer_fees`) VALUES
(1, 'ProFelar - Social Boosting Platform', 'ProFelar - Social Boosting Platform', 'Best and Cheap SMM Panel for Instagram, Tiktok, Facebook, Youtube and Twitter. Buy IG Reels views and Followers, Buy Instagram Likes, Views and Comments, Buy TikTok Likes and Followers, Buy Facebook Likes and Comments, Buy Youtube Likes, Views and Subscribers.\r\n', 'ProFelar - Social Boosting Platform, smm panel,smmpanel,SMM Panel India,SMM Panel Paytm,SMM Panel Cheap India,SMM Reseller Panel,SMM Reseller Panel India,Cheap SMM Panel,cheapest SMM panel,cheap SMM panel india,Cheapest SMM Reseller Panel,Cheapest SMM Panel Paytm,Cheapest SMM Panel Paytm,indian smm panel,IndianSMM Reseller Panel,Best SMM panel,Best SMM Panel India,Top SMM Panel', 'public/images/b1d10e7bafa4421218a51b1e1f1b0ba2.png', 'PROFELAR', 'USD', '', 'en', 'salzemedia', 'Blue', '1', '6LfQ414eAAAAAD0B3Nx7vmhg3rw8Ae7T-4dfI1ii', '6LfQ414eAAAAAL3jYAvNPi5xJJ6M89CcdFFxritH', '', '<!-- CODE START --> \r\n<!-- WhatsApp Chat Plugin Code by : VCreato Team. --->\r\n<style>.integration-fixed{position:fixed;z-index:10000000}.integration-fixed__top-left{top:0;left:0}.integration-fixed__top-right{top:0;right:0}.integration-fixed__bottom-left{bottom:0;left:0}.integration-fixed__bottom-right{bottom:0;right:0}\r\n.whatsapp-container{padding:24px}.whatsapp-button{width:60px;height:60px;bottom:40px;right:40px;background-color:#25d366;color:#FFF!important;border-radius:50px;text-align:center;font-size:30px;box-shadow:2px 2px 3px #999;display:flex;align-items:center;justify-content:center;text-decoration:none!important;-webkit-transition:all 0.3s ease;-moz-transition:all 0.3s ease;-o-transition:all 0.3s ease;-ms-transition:all 0.3s ease;transition:all 0.3s ease;transform:scale(0.9)}.whatsapp-button:hover{transform:scale(1);background-color:#1fcc5f}\r\n</style>\r\n\r\n<div class=\"integration-fixed integration-fixed__bottom-right \">\r\n    <div class=\"whatsapp-container \">\r\n        <a href=\"https://wa.me/9424518360 \" target=\"_blank \" class=\"whatsapp-button \">\r\n            <i class=\"fab fa-whatsapp \"></i>\r\n        </a>\r\n    </div>\r\n</div>\r\n<!-- CODE END -->', '1', '2', '1', '2', 0, 0, 'support@smmprofessional.com', 'Abdoqweqwe123', 'mail.smmprofessional.com', '465', 'tls', '2', '2', '2', '2', '2', '2', 'bizimsms', '', '', '', '1', 'support@smmprofessional.com', '', '2', '1', '2', '2', 'asc', 500, 2500, 10000, 15000, 'ns1.fukrahost.com', 'ns2.fukrahost.com', 1, '', '', '2', 5, 10, '2', '2', 10, '1', '2', '$', '₹', 74.87, '$', 0.013, '0', '1', '1', '2', '2', '1', 0, '2', '2', 2, 191530, 200022, '0', '3');

-- --------------------------------------------------------

--
-- Table structure for table `sync_logs`
--

CREATE TABLE `sync_logs` (
  `id` int(11) NOT NULL,
  `service_id` int(11) NOT NULL,
  `action` varchar(225) NOT NULL,
  `date` datetime NOT NULL,
  `description` varchar(225) NOT NULL,
  `api_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `sync_logs`
--

INSERT INTO `sync_logs` (`id`, `service_id`, `action`, `date`, `description`, `api_id`) VALUES
(1, 4742, 'Price Changed on\r\nprovider from 11.65 to 11.49', '2022-07-30 21:25:26', 'Price changed from 11.65 to 11.49', 6),
(2, 4742, 'Service Removed on provider', '2022-07-30 22:20:12', 'Deactivated Service', 6),
(3, 4742, 'Service Reactivated on provider', '2022-07-30 22:25:45', 'Activated Service', 6),
(4, 4743, 'Service Removed on provider', '2022-08-03 20:20:11', 'Deactivated Service', 5),
(5, 4743, 'Service Reactivated on provider', '2022-08-03 20:25:43', 'Activated Service', 5),
(6, 4743, 'Service Removed on provider', '2022-08-03 20:52:03', 'Deactivated Service', 5),
(7, 4743, 'Service Reactivated on provider', '2022-08-03 20:53:03', 'Activated Service', 5),
(8, 4743, 'Service Removed on provider', '2022-08-03 21:00:03', 'Deactivated Service', 5),
(9, 4743, 'Service Reactivated on provider', '2022-08-03 21:01:03', 'Activated Service', 5),
(10, 4752, 'Service Removed on provider', '2022-08-03 21:11:03', 'Deactivated Service', 9),
(11, 4744, 'Price Changed on\r\nprovider from 11.49 to 14.48', '2022-08-03 21:11:03', 'Price changed from 11.49 to 14.48', 9),
(12, 4752, 'Service Reactivated on provider', '2022-08-03 21:12:02', 'Activated Service', 9),
(13, 4752, 'Service Removed on provider', '2022-08-03 21:16:03', 'Deactivated Service', 9),
(14, 4752, 'Service Reactivated on provider', '2022-08-03 21:17:03', 'Activated Service', 9),
(15, 4751, 'Service Removed on provider', '2022-08-03 21:21:02', 'Deactivated Service', 9),
(16, 4751, 'Service Reactivated on provider', '2022-08-03 21:22:03', 'Activated Service', 9),
(17, 4743, 'Service Removed on provider', '2022-08-03 21:31:02', 'Deactivated Service', 5),
(18, 4745, 'Service Removed on provider', '2022-08-03 21:31:02', 'Deactivated Service', 9),
(19, 4746, 'Service Removed on provider', '2022-08-03 21:31:02', 'Deactivated Service', 9),
(20, 4747, 'Service Removed on provider', '2022-08-03 21:31:02', 'Deactivated Service', 9),
(21, 4751, 'Service Removed on provider', '2022-08-03 21:31:02', 'Deactivated Service', 9),
(22, 4753, 'Service Removed on provider', '2022-08-03 21:31:02', 'Deactivated Service', 9),
(23, 4743, 'Service Reactivated on provider', '2022-08-03 21:32:02', 'Activated Service', 5),
(24, 4746, 'Service Reactivated on provider', '2022-08-03 21:32:02', 'Activated Service', 9),
(25, 4747, 'Service Reactivated on provider', '2022-08-03 21:32:02', 'Activated Service', 9),
(26, 4751, 'Service Reactivated on provider', '2022-08-03 21:32:02', 'Activated Service', 9),
(27, 4753, 'Service Reactivated on provider', '2022-08-03 21:32:02', 'Activated Service', 9),
(28, 4745, 'Service Reactivated on provider', '2022-08-03 21:33:03', 'Activated Service', 9),
(29, 4753, 'Service Removed on provider', '2022-08-03 21:52:03', 'Deactivated Service', 9),
(30, 4753, 'Service Reactivated on provider', '2022-08-03 21:53:03', 'Activated Service', 9),
(31, 4748, 'Service Removed on provider', '2022-08-03 21:56:03', 'Deactivated Service', 9),
(32, 4748, 'Service Reactivated on provider', '2022-08-03 21:57:03', 'Activated Service', 9),
(33, 4752, 'Service Removed on provider', '2022-08-03 22:04:03', 'Deactivated Service', 9),
(34, 4752, 'Service Reactivated on provider', '2022-08-03 22:05:04', 'Activated Service', 9),
(35, 4753, 'Service Removed on provider', '2022-08-03 22:06:03', 'Deactivated Service', 9),
(36, 4753, 'Service Reactivated on provider', '2022-08-03 22:07:03', 'Activated Service', 9),
(37, 4743, 'Service Removed on provider', '2022-08-03 22:09:03', 'Deactivated Service', 5),
(38, 4752, 'Service Removed on provider', '2022-08-03 22:09:03', 'Deactivated Service', 9),
(39, 4753, 'Service Removed on provider', '2022-08-03 22:09:03', 'Deactivated Service', 9),
(40, 4744, 'Service Removed on provider', '2022-08-03 22:09:03', 'Deactivated Service', 9),
(41, 4747, 'Service Removed on provider', '2022-08-03 22:09:03', 'Deactivated Service', 9),
(42, 4745, 'Service Removed on provider', '2022-08-03 22:10:03', 'Deactivated Service', 9),
(43, 4746, 'Service Removed on provider', '2022-08-03 22:10:03', 'Deactivated Service', 9),
(44, 4750, 'Service Removed on provider', '2022-08-03 22:10:03', 'Deactivated Service', 9),
(45, 4751, 'Service Removed on provider', '2022-08-03 22:10:03', 'Deactivated Service', 9),
(46, 4743, 'Service Reactivated on provider', '2022-08-03 22:10:03', 'Activated Service', 5),
(47, 4753, 'Service Reactivated on provider', '2022-08-03 22:10:03', 'Activated Service', 9),
(48, 4746, 'Service Reactivated on provider', '2022-08-03 22:11:03', 'Activated Service', 9),
(49, 4751, 'Service Reactivated on provider', '2022-08-03 22:11:03', 'Activated Service', 9),
(50, 4745, 'Service Reactivated on provider', '2022-08-03 22:12:03', 'Activated Service', 9),
(51, 4750, 'Service Reactivated on provider', '2022-08-03 22:12:03', 'Activated Service', 9),
(52, 4752, 'Service Reactivated on provider', '2022-08-03 22:12:03', 'Activated Service', 9),
(53, 4743, 'Service Removed on provider', '2022-08-03 22:14:02', 'Deactivated Service', 5),
(54, 4744, 'Service Removed on provider', '2022-08-03 22:15:04', 'Deactivated Service', 9),
(55, 4743, 'Service Reactivated on provider', '2022-08-03 22:15:04', 'Activated Service', 5),
(56, 4744, 'Service Reactivated on provider', '2022-08-03 22:16:02', 'Activated Service', 9),
(57, 4752, 'Service Removed on provider', '2022-08-03 22:22:02', 'Deactivated Service', 9),
(58, 4753, 'Service Removed on provider', '2022-08-03 22:22:02', 'Deactivated Service', 9),
(59, 4752, 'Service Reactivated on provider', '2022-08-03 22:23:04', 'Activated Service', 9),
(60, 4753, 'Service Reactivated on provider', '2022-08-03 22:23:04', 'Activated Service', 9),
(61, 4743, 'Service Removed on provider', '2022-08-03 23:31:13', 'Deactivated Service', 5),
(62, 4749, 'Service Removed on provider', '2022-08-03 23:32:02', 'Deactivated Service', 9),
(63, 4747, 'Service Removed on provider', '2022-08-03 23:32:02', 'Deactivated Service', 9),
(64, 4744, 'Service Removed on provider', '2022-08-03 23:32:02', 'Deactivated Service', 9),
(65, 4746, 'Service Removed on provider', '2022-08-03 23:32:02', 'Deactivated Service', 9),
(66, 4753, 'Service Removed on provider', '2022-08-03 23:33:02', 'Deactivated Service', 9),
(67, 4749, 'Service Reactivated on provider', '2022-08-03 23:33:02', 'Activated Service', 9),
(68, 4743, 'Service Reactivated on provider', '2022-08-03 23:33:02', 'Activated Service', 5),
(69, 4752, 'Service Removed on provider', '2022-08-03 23:34:03', 'Deactivated Service', 9),
(70, 4752, 'Service Reactivated on provider', '2022-08-03 23:35:04', 'Activated Service', 9),
(71, 4753, 'Service Reactivated on provider', '2022-08-03 23:35:04', 'Activated Service', 9),
(72, 4748, 'Service Removed on provider', '2022-08-03 23:37:03', 'Deactivated Service', 9),
(73, 4748, 'Service Reactivated on provider', '2022-08-03 23:38:02', 'Activated Service', 9),
(74, 4751, 'Service Removed on provider', '2022-08-03 23:39:02', 'Deactivated Service', 9),
(75, 4743, 'Service Removed on provider', '2022-08-03 23:40:03', 'Deactivated Service', 5),
(76, 4743, 'Service Reactivated on provider', '2022-08-03 23:41:03', 'Activated Service', 5),
(77, 4747, 'Service Removed on provider', '2022-08-03 23:42:03', 'Deactivated Service', 9),
(78, 4751, 'Service Reactivated on provider', '2022-08-03 23:42:03', 'Activated Service', 9),
(79, 4747, 'Service Reactivated on provider', '2022-08-03 23:43:03', 'Activated Service', 9),
(80, 4752, 'Service Removed on provider', '2022-08-03 23:49:03', 'Deactivated Service', 9),
(81, 4752, 'Service Reactivated on provider', '2022-08-03 23:50:04', 'Activated Service', 9),
(82, 4752, 'Service Removed on provider', '2022-08-04 00:53:51', 'Deactivated Service', 9),
(83, 4752, 'Service Removed on provider', '2022-08-04 01:24:18', 'Deactivated Service', 9),
(84, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:29', 'Activated Service', 9),
(85, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:29', 'Activated Service', 9),
(86, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:29', 'Activated Service', 9),
(87, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:43', 'Activated Service', 9),
(88, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:43', 'Activated Service', 9),
(89, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:43', 'Activated Service', 9),
(90, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:43', 'Activated Service', 9),
(91, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:43', 'Activated Service', 9),
(92, 4752, 'Service Reactivated on provider', '2022-08-04 01:24:43', 'Activated Service', 9),
(93, 4752, 'Service Removed on provider', '2022-08-04 01:55:09', 'Deactivated Service', 9),
(94, 4752, 'Service Reactivated on provider', '2022-08-04 01:55:16', 'Activated Service', 9),
(95, 4752, 'Service Reactivated on provider', '2022-08-04 01:55:22', 'Activated Service', 9),
(96, 4752, 'Service Reactivated on provider', '2022-08-04 01:55:22', 'Activated Service', 9),
(97, 4752, 'Service Reactivated on provider', '2022-08-04 01:55:25', 'Activated Service', 9),
(98, 4743, 'Service Removed on provider', '2022-08-04 01:56:01', 'Deactivated Service', 5),
(99, 4745, 'Service Removed on provider', '2022-08-04 01:56:01', 'Deactivated Service', 9),
(100, 4752, 'Service Removed on provider', '2022-08-04 01:56:01', 'Deactivated Service', 9),
(101, 4753, 'Service Removed on provider', '2022-08-04 01:56:01', 'Deactivated Service', 9),
(102, 4743, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 5),
(103, 4747, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(104, 4749, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(105, 4745, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(106, 4751, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(107, 4753, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(108, 4744, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(109, 4748, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(110, 4752, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(111, 4753, 'Service Reactivated on provider', '2022-08-04 01:56:23', 'Activated Service', 9),
(112, 4752, 'Service Reactivated on provider', '2022-08-04 01:56:23', 'Activated Service', 9),
(113, 4748, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(114, 4750, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(115, 4753, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(116, 4743, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 5),
(117, 4746, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(118, 4753, 'Service Reactivated on provider', '2022-08-04 01:56:23', 'Activated Service', 9),
(119, 4752, 'Service Reactivated on provider', '2022-08-04 01:56:23', 'Activated Service', 9),
(120, 4753, 'Service Reactivated on provider', '2022-08-04 01:56:23', 'Activated Service', 9),
(121, 4744, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(122, 4749, 'Service Removed on provider', '2022-08-04 01:56:23', 'Deactivated Service', 9),
(123, 4743, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 5),
(124, 4745, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(125, 4744, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 9),
(126, 4743, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 5),
(127, 4743, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 5),
(128, 4750, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(129, 4752, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(130, 4744, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(131, 4746, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(132, 4743, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 5),
(133, 4747, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(134, 4748, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(135, 4745, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(136, 4749, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(137, 4750, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(138, 4753, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(139, 4743, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 5),
(140, 4743, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 5),
(141, 4744, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(142, 4746, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(143, 4746, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 9),
(144, 4746, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(145, 4748, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(146, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 9),
(147, 4748, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(148, 4751, 'Service Removed on provider', '2022-08-04 02:27:01', 'Deactivated Service', 9),
(149, 4743, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 5),
(150, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 9),
(151, 4753, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 9),
(152, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 9),
(153, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:01', 'Activated Service', 9),
(154, 4753, 'Service Reactivated on provider', '2022-08-04 02:27:06', 'Activated Service', 9),
(155, 4753, 'Service Reactivated on provider', '2022-08-04 02:27:06', 'Activated Service', 9),
(156, 4752, 'Service Reactivated on provider', '2022-08-04 02:27:08', 'Activated Service', 9),
(157, 4753, 'Service Reactivated on provider', '2022-08-04 02:27:08', 'Activated Service', 9),
(158, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:14', 'Activated Service', 9),
(159, 4752, 'Service Reactivated on provider', '2022-08-04 02:27:14', 'Activated Service', 9),
(160, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:14', 'Activated Service', 9),
(161, 4752, 'Service Reactivated on provider', '2022-08-04 02:27:14', 'Activated Service', 9),
(162, 4752, 'Service Reactivated on provider', '2022-08-04 02:27:14', 'Activated Service', 9),
(163, 4752, 'Service Reactivated on provider', '2022-08-04 02:27:14', 'Activated Service', 9),
(164, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:22', 'Activated Service', 9),
(165, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:22', 'Activated Service', 9),
(166, 4752, 'Service Reactivated on provider', '2022-08-04 02:27:22', 'Activated Service', 9),
(167, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:22', 'Activated Service', 9),
(168, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:22', 'Activated Service', 9),
(169, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:26', 'Activated Service', 9),
(170, 4750, 'Service Reactivated on provider', '2022-08-04 02:27:26', 'Activated Service', 9),
(171, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:26', 'Activated Service', 9),
(172, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:29', 'Activated Service', 9),
(173, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:29', 'Activated Service', 9),
(174, 4746, 'Service Reactivated on provider', '2022-08-04 02:27:29', 'Activated Service', 9),
(175, 4746, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(176, 4746, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(177, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(178, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(179, 4749, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(180, 4745, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(181, 4745, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(182, 4746, 'Service Reactivated on provider', '2022-08-04 02:27:40', 'Activated Service', 9),
(183, 4745, 'Service Reactivated on provider', '2022-08-04 02:27:44', 'Activated Service', 9),
(184, 4746, 'Service Reactivated on provider', '2022-08-04 02:27:44', 'Activated Service', 9),
(185, 4743, 'Service Reactivated on provider', '2022-08-04 02:27:44', 'Activated Service', 5),
(186, 4745, 'Service Reactivated on provider', '2022-08-04 02:27:44', 'Activated Service', 9),
(187, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(188, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 5),
(189, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 5),
(190, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 5),
(191, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(192, 4746, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(193, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(194, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 5),
(195, 4746, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(196, 4746, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(197, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(198, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 5),
(199, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(200, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 9),
(201, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:02', 'Activated Service', 5),
(202, 4746, 'Service Reactivated on provider', '2022-08-04 02:28:03', 'Activated Service', 9),
(203, 4746, 'Service Reactivated on provider', '2022-08-04 02:28:03', 'Activated Service', 9),
(204, 4746, 'Service Reactivated on provider', '2022-08-04 02:28:03', 'Activated Service', 9),
(205, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:03', 'Activated Service', 9),
(206, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:03', 'Activated Service', 5),
(207, 4745, 'Service Reactivated on provider', '2022-08-04 02:28:04', 'Activated Service', 9),
(208, 4743, 'Service Reactivated on provider', '2022-08-04 02:28:04', 'Activated Service', 5),
(209, 4743, 'Service Reactivated on provider', '2022-08-04 02:29:03', 'Activated Service', 5),
(210, 4743, 'Service Reactivated on provider', '2022-08-04 02:29:03', 'Activated Service', 5),
(211, 4743, 'Service Reactivated on provider', '2022-08-04 02:29:03', 'Activated Service', 5),
(212, 4743, 'Service Reactivated on provider', '2022-08-04 02:29:03', 'Activated Service', 5),
(213, 4743, 'Service Reactivated on provider', '2022-08-04 02:29:03', 'Activated Service', 5),
(214, 4743, 'Service Reactivated on provider', '2022-08-04 02:29:03', 'Activated Service', 5),
(215, 4751, 'Service Removed on provider', '2022-08-04 02:33:03', 'Deactivated Service', 9),
(216, 4751, 'Service Reactivated on provider', '2022-08-04 02:34:03', 'Activated Service', 9),
(217, 4745, 'Service Removed on provider', '2022-08-04 03:34:57', 'Deactivated Service', 9),
(218, 4752, 'Service Removed on provider', '2022-08-04 03:36:03', 'Deactivated Service', 9),
(219, 4753, 'Service Removed on provider', '2022-08-04 04:06:22', 'Deactivated Service', 9),
(220, 4748, 'Service Removed on provider', '2022-08-04 04:06:22', 'Deactivated Service', 9),
(221, 4743, 'Service Removed on provider', '2022-08-04 04:06:22', 'Deactivated Service', 5),
(222, 4753, 'Service Reactivated on provider', '2022-08-04 04:06:29', 'Activated Service', 9),
(223, 4753, 'Service Reactivated on provider', '2022-08-04 04:06:29', 'Activated Service', 9),
(224, 4753, 'Service Reactivated on provider', '2022-08-04 04:06:30', 'Activated Service', 9),
(225, 4753, 'Service Reactivated on provider', '2022-08-04 04:06:34', 'Activated Service', 9),
(226, 4753, 'Service Reactivated on provider', '2022-08-04 04:06:34', 'Activated Service', 9),
(227, 4745, 'Service Removed on provider', '2022-08-04 04:07:23', 'Deactivated Service', 9),
(228, 4743, 'Service Removed on provider', '2022-08-04 04:11:03', 'Deactivated Service', 5),
(229, 4746, 'Service Removed on provider', '2022-08-04 04:11:03', 'Deactivated Service', 9),
(230, 4747, 'Service Removed on provider', '2022-08-04 04:11:03', 'Deactivated Service', 9),
(231, 4750, 'Service Removed on provider', '2022-08-04 04:11:03', 'Deactivated Service', 9),
(232, 4751, 'Service Removed on provider', '2022-08-04 04:11:03', 'Deactivated Service', 9),
(233, 4744, 'Service Removed on provider', '2022-08-04 04:41:23', 'Deactivated Service', 9),
(234, 4745, 'Service Removed on provider', '2022-08-04 04:41:23', 'Deactivated Service', 9),
(235, 4748, 'Service Removed on provider', '2022-08-04 04:41:23', 'Deactivated Service', 9),
(236, 4752, 'Service Removed on provider', '2022-08-04 04:41:23', 'Deactivated Service', 9),
(237, 4753, 'Service Removed on provider', '2022-08-04 04:41:23', 'Deactivated Service', 9),
(238, 4753, 'Service Reactivated on provider', '2022-08-04 04:41:30', 'Activated Service', 9),
(239, 4753, 'Service Reactivated on provider', '2022-08-04 04:41:30', 'Activated Service', 9),
(240, 4751, 'Service Reactivated on provider', '2022-08-04 04:41:35', 'Activated Service', 9),
(241, 4752, 'Service Reactivated on provider', '2022-08-04 04:41:35', 'Activated Service', 9),
(242, 4752, 'Service Reactivated on provider', '2022-08-04 04:41:35', 'Activated Service', 9),
(243, 4753, 'Service Reactivated on provider', '2022-08-04 04:41:35', 'Activated Service', 9),
(244, 4752, 'Service Reactivated on provider', '2022-08-04 04:41:35', 'Activated Service', 9),
(245, 4751, 'Service Reactivated on provider', '2022-08-04 04:41:37', 'Activated Service', 9),
(246, 4751, 'Service Reactivated on provider', '2022-08-04 04:41:37', 'Activated Service', 9),
(247, 4752, 'Service Reactivated on provider', '2022-08-04 04:41:40', 'Activated Service', 9),
(248, 4750, 'Service Reactivated on provider', '2022-08-04 04:41:40', 'Activated Service', 9),
(249, 4752, 'Service Reactivated on provider', '2022-08-04 04:41:40', 'Activated Service', 9),
(250, 4750, 'Service Reactivated on provider', '2022-08-04 04:41:41', 'Activated Service', 9),
(251, 4751, 'Service Reactivated on provider', '2022-08-04 04:41:44', 'Activated Service', 9),
(252, 4751, 'Service Reactivated on provider', '2022-08-04 04:41:44', 'Activated Service', 9),
(253, 4750, 'Service Reactivated on provider', '2022-08-04 04:41:44', 'Activated Service', 9),
(254, 4750, 'Service Reactivated on provider', '2022-08-04 04:41:47', 'Activated Service', 9),
(255, 4750, 'Service Reactivated on provider', '2022-08-04 04:41:47', 'Activated Service', 9),
(256, 4748, 'Service Reactivated on provider', '2022-08-04 04:41:47', 'Activated Service', 9),
(257, 4748, 'Service Reactivated on provider', '2022-08-04 04:41:48', 'Activated Service', 9),
(258, 4747, 'Service Reactivated on provider', '2022-08-04 04:41:48', 'Activated Service', 9),
(259, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(260, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(261, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 5),
(262, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(263, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(264, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(265, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(266, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(267, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(268, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(269, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(270, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(271, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(272, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(273, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(274, 4750, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(275, 4750, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(276, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(277, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(278, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:01', 'Activated Service', 9),
(279, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:02', 'Activated Service', 9),
(280, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:02', 'Activated Service', 9),
(281, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:02', 'Activated Service', 9),
(282, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:02', 'Activated Service', 9),
(283, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(284, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(285, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(286, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 5),
(287, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(288, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(289, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(290, 4748, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(291, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 5),
(292, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(293, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(294, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(295, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(296, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(297, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(298, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:12', 'Activated Service', 9),
(299, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 5),
(300, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(301, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(302, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(303, 4745, 'Service Removed on provider', '2022-08-04 04:42:21', 'Deactivated Service', 9),
(304, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 5),
(305, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 5),
(306, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(307, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(308, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(309, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(310, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(311, 4747, 'Service Reactivated on provider', '2022-08-04 04:42:21', 'Activated Service', 9),
(312, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:24', 'Activated Service', 9),
(313, 4746, 'Service Reactivated on provider', '2022-08-04 04:42:24', 'Activated Service', 9),
(314, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:24', 'Activated Service', 5),
(315, 4743, 'Service Reactivated on provider', '2022-08-04 04:42:24', 'Activated Service', 5),
(316, 4745, 'Service Reactivated on provider', '2022-08-04 04:42:24', 'Activated Service', 9),
(317, 4744, 'Service Reactivated on provider', '2022-08-04 04:42:24', 'Activated Service', 9),
(318, 4745, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 9),
(319, 4743, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 5),
(320, 4743, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 5),
(321, 4747, 'Service Removed on provider', '2022-08-04 05:12:45', 'Deactivated Service', 9),
(322, 4743, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 5),
(323, 4744, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 9),
(324, 4743, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 5),
(325, 4745, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 9),
(326, 4744, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 9),
(327, 4744, 'Service Reactivated on provider', '2022-08-04 05:12:45', 'Activated Service', 9),
(328, 4746, 'Service Removed on provider', '2022-08-04 05:45:22', 'Deactivated Service', 9),
(329, 4753, 'Service Removed on provider', '2022-08-04 06:15:39', 'Deactivated Service', 9),
(330, 4751, 'Service Removed on provider', '2022-08-04 06:15:39', 'Deactivated Service', 9),
(331, 4748, 'Service Removed on provider', '2022-08-04 06:15:39', 'Deactivated Service', 9),
(332, 4751, 'Service Reactivated on provider', '2022-08-04 06:15:45', 'Activated Service', 9),
(333, 4751, 'Service Reactivated on provider', '2022-08-04 06:15:47', 'Activated Service', 9),
(334, 4751, 'Service Reactivated on provider', '2022-08-04 06:15:47', 'Activated Service', 9),
(335, 4753, 'Service Reactivated on provider', '2022-08-04 06:15:47', 'Activated Service', 9),
(336, 4751, 'Service Reactivated on provider', '2022-08-04 06:16:03', 'Activated Service', 9),
(337, 4751, 'Service Reactivated on provider', '2022-08-04 06:16:03', 'Activated Service', 9),
(338, 4753, 'Service Reactivated on provider', '2022-08-04 06:16:03', 'Activated Service', 9),
(339, 4753, 'Service Reactivated on provider', '2022-08-04 06:16:03', 'Activated Service', 9),
(340, 4744, 'Service Removed on provider', '2022-08-04 06:16:12', 'Deactivated Service', 9),
(341, 4745, 'Service Removed on provider', '2022-08-04 06:16:12', 'Deactivated Service', 9),
(342, 4747, 'Service Removed on provider', '2022-08-04 06:16:12', 'Deactivated Service', 9),
(343, 4748, 'Service Removed on provider', '2022-08-04 06:16:12', 'Deactivated Service', 9),
(344, 4749, 'Service Removed on provider', '2022-08-04 06:16:12', 'Deactivated Service', 9),
(345, 4752, 'Service Removed on provider', '2022-08-04 06:16:12', 'Deactivated Service', 9),
(346, 4753, 'Service Removed on provider', '2022-08-04 06:16:12', 'Deactivated Service', 9),
(347, 4747, 'Service Removed on provider', '2022-08-04 06:16:21', 'Deactivated Service', 9),
(348, 4750, 'Service Removed on provider', '2022-08-04 06:16:21', 'Deactivated Service', 9),
(349, 4752, 'Service Removed on provider', '2022-08-04 06:16:21', 'Deactivated Service', 9),
(350, 4753, 'Service Reactivated on provider', '2022-08-04 06:16:24', 'Activated Service', 9),
(351, 4743, 'Service Removed on provider', '2022-08-04 06:16:24', 'Deactivated Service', 5),
(352, 4751, 'Service Removed on provider', '2022-08-04 06:16:24', 'Deactivated Service', 9),
(353, 4752, 'Service Reactivated on provider', '2022-08-04 06:16:32', 'Activated Service', 9),
(354, 4745, 'Service Removed on provider', '2022-08-04 06:16:32', 'Deactivated Service', 9),
(355, 4753, 'Service Removed on provider', '2022-08-04 06:16:32', 'Deactivated Service', 9),
(356, 4752, 'Service Removed on provider', '2022-08-04 06:16:42', 'Deactivated Service', 9),
(357, 4752, 'Service Reactivated on provider', '2022-08-04 06:16:42', 'Activated Service', 9),
(358, 4748, 'Service Removed on provider', '2022-08-04 06:16:46', 'Deactivated Service', 9),
(359, 4750, 'Service Removed on provider', '2022-08-04 06:16:46', 'Deactivated Service', 9),
(360, 4753, 'Service Reactivated on provider', '2022-08-04 06:16:46', 'Activated Service', 9),
(361, 4745, 'Service Removed on provider', '2022-08-04 06:46:55', 'Deactivated Service', 9),
(362, 4748, 'Service Removed on provider', '2022-08-04 06:46:55', 'Deactivated Service', 9),
(363, 4748, 'Service Reactivated on provider', '2022-08-04 06:46:55', 'Activated Service', 9),
(364, 4746, 'Service Removed on provider', '2022-08-04 06:46:55', 'Deactivated Service', 9),
(365, 4751, 'Service Removed on provider', '2022-08-04 06:46:55', 'Deactivated Service', 9),
(366, 4743, 'Service Reactivated on provider', '2022-08-04 06:46:55', 'Activated Service', 5),
(367, 4750, 'Service Reactivated on provider', '2022-08-04 06:46:55', 'Activated Service', 9),
(368, 4745, 'Service Removed on provider', '2022-08-04 06:46:55', 'Deactivated Service', 9),
(369, 4749, 'Service Removed on provider', '2022-08-04 06:46:55', 'Deactivated Service', 9),
(370, 4753, 'Service Removed on provider', '2022-08-04 06:46:55', 'Deactivated Service', 9),
(371, 4752, 'Service Reactivated on provider', '2022-08-04 06:46:55', 'Activated Service', 9),
(372, 4747, 'Service Reactivated on provider', '2022-08-04 06:46:55', 'Activated Service', 9),
(373, 4747, 'Service Reactivated on provider', '2022-08-04 06:46:55', 'Activated Service', 9),
(374, 4752, 'Service Reactivated on provider', '2022-08-04 06:46:55', 'Activated Service', 9),
(375, 4753, 'Service Reactivated on provider', '2022-08-04 06:46:57', 'Activated Service', 9),
(376, 4753, 'Service Reactivated on provider', '2022-08-04 06:47:02', 'Activated Service', 9),
(377, 4753, 'Service Reactivated on provider', '2022-08-04 06:47:02', 'Activated Service', 9),
(378, 4753, 'Service Reactivated on provider', '2022-08-04 06:47:02', 'Activated Service', 9),
(379, 4753, 'Service Reactivated on provider', '2022-08-04 06:47:02', 'Activated Service', 9),
(380, 4753, 'Service Reactivated on provider', '2022-08-04 06:47:02', 'Activated Service', 9),
(381, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:05', 'Activated Service', 9),
(382, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:07', 'Activated Service', 9),
(383, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:09', 'Activated Service', 9),
(384, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:09', 'Activated Service', 9),
(385, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:09', 'Activated Service', 9),
(386, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:13', 'Activated Service', 9),
(387, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:13', 'Activated Service', 9),
(388, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:21', 'Activated Service', 9),
(389, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:21', 'Activated Service', 9),
(390, 4751, 'Service Reactivated on provider', '2022-08-04 06:47:21', 'Activated Service', 9),
(391, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:21', 'Activated Service', 9),
(392, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:24', 'Activated Service', 9),
(393, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:24', 'Activated Service', 9),
(394, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:24', 'Activated Service', 9),
(395, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(396, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(397, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(398, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(399, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(400, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(401, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(402, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(403, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(404, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(405, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(406, 4748, 'Service Reactivated on provider', '2022-08-04 06:47:43', 'Activated Service', 9),
(407, 4745, 'Service Reactivated on provider', '2022-08-04 06:47:46', 'Activated Service', 9),
(408, 4745, 'Service Reactivated on provider', '2022-08-04 06:48:02', 'Activated Service', 9),
(409, 4745, 'Service Reactivated on provider', '2022-08-04 06:48:02', 'Activated Service', 9),
(410, 4753, 'Service Removed on provider', '2022-08-04 06:48:02', 'Deactivated Service', 9),
(411, 4745, 'Service Reactivated on provider', '2022-08-04 06:48:02', 'Activated Service', 9),
(412, 4745, 'Service Reactivated on provider', '2022-08-04 06:48:02', 'Activated Service', 9),
(413, 4745, 'Service Reactivated on provider', '2022-08-04 06:48:02', 'Activated Service', 9),
(414, 4753, 'Service Reactivated on provider', '2022-08-04 06:49:02', 'Activated Service', 9),
(415, 4753, 'Service Reactivated on provider', '2022-08-04 06:49:02', 'Activated Service', 9),
(416, 4753, 'Service Reactivated on provider', '2022-08-04 06:49:02', 'Activated Service', 9),
(417, 4750, 'Service Removed on provider', '2022-08-04 07:22:28', 'Deactivated Service', 9),
(418, 4750, 'Service Reactivated on provider', '2022-08-04 07:22:40', 'Activated Service', 9),
(419, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(420, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(421, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(422, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(423, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(424, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(425, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(426, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(427, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(428, 4750, 'Service Reactivated on provider', '2022-08-04 07:23:03', 'Activated Service', 9),
(429, 4753, 'Service Removed on provider', '2022-08-04 07:23:23', 'Deactivated Service', 9),
(430, 4743, 'Service Removed on provider', '2022-08-04 07:23:23', 'Deactivated Service', 5),
(431, 4753, 'Service Reactivated on provider', '2022-08-04 07:23:40', 'Activated Service', 9),
(432, 4747, 'Service Removed on provider', '2022-08-04 07:23:40', 'Deactivated Service', 9),
(433, 4753, 'Service Reactivated on provider', '2022-08-04 07:23:40', 'Activated Service', 9),
(434, 4743, 'Service Reactivated on provider', '2022-08-04 07:24:02', 'Activated Service', 5),
(435, 4753, 'Service Removed on provider', '2022-08-04 07:24:02', 'Deactivated Service', 9),
(436, 4753, 'Service Reactivated on provider', '2022-08-04 07:54:35', 'Activated Service', 9),
(437, 4749, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(438, 4752, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(439, 4744, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(440, 4748, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(441, 4747, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(442, 4751, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(443, 4753, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(444, 4746, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(445, 4749, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(446, 4751, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(447, 4753, 'Service Removed on provider', '2022-08-04 08:25:24', 'Deactivated Service', 9),
(448, 4753, 'Service Reactivated on provider', '2022-08-04 08:25:29', 'Activated Service', 9),
(449, 4752, 'Service Reactivated on provider', '2022-08-04 08:25:30', 'Activated Service', 9),
(450, 4751, 'Service Reactivated on provider', '2022-08-04 08:25:34', 'Activated Service', 9),
(451, 4749, 'Service Reactivated on provider', '2022-08-04 08:25:36', 'Activated Service', 9),
(452, 4749, 'Service Reactivated on provider', '2022-08-04 08:25:43', 'Activated Service', 9),
(453, 4749, 'Service Reactivated on provider', '2022-08-04 08:25:50', 'Activated Service', 9),
(454, 4743, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 5),
(455, 4748, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 9),
(456, 4749, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 9),
(457, 4750, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 9),
(458, 4745, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 9),
(459, 4751, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 9),
(460, 4752, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 9),
(461, 4753, 'Service Removed on provider', '2022-08-04 08:25:54', 'Deactivated Service', 9),
(462, 4744, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(463, 4749, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(464, 4745, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(465, 4746, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(466, 4747, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(467, 4748, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(468, 4749, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(469, 4751, 'Service Removed on provider', '2022-08-04 08:26:02', 'Deactivated Service', 9),
(470, 4749, 'Service Reactivated on provider', '2022-08-04 08:26:02', 'Activated Service', 9),
(471, 4748, 'Service Removed on provider', '2022-08-04 08:26:04', 'Deactivated Service', 9),
(472, 4749, 'Service Reactivated on provider', '2022-08-04 08:26:15', 'Activated Service', 9),
(473, 4753, 'Service Reactivated on provider', '2022-08-04 08:26:15', 'Activated Service', 9),
(474, 4744, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(475, 4745, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(476, 4751, 'Service Reactivated on provider', '2022-08-04 08:26:15', 'Activated Service', 9),
(477, 4743, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 5),
(478, 4745, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(479, 4747, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(480, 4749, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(481, 4752, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(482, 4752, 'Service Reactivated on provider', '2022-08-04 08:26:15', 'Activated Service', 9),
(483, 4747, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(484, 4753, 'Service Removed on provider', '2022-08-04 08:26:15', 'Deactivated Service', 9),
(485, 4753, 'Service Reactivated on provider', '2022-08-04 08:26:15', 'Activated Service', 9),
(486, 4746, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(487, 4743, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 5),
(488, 4749, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(489, 4745, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(490, 4747, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(491, 4749, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(492, 4750, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(493, 4752, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(494, 4743, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 5),
(495, 4745, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(496, 4747, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(497, 4750, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(498, 4748, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(499, 4751, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(500, 4743, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 5),
(501, 4748, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(502, 4750, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(503, 4751, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(504, 4749, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(505, 4752, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(506, 4750, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(507, 4751, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(508, 4749, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(509, 4752, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(510, 4753, 'Service Removed on provider', '2022-08-04 08:56:27', 'Deactivated Service', 9),
(511, 4752, 'Service Reactivated on provider', '2022-08-04 08:56:27', 'Activated Service', 9),
(512, 4753, 'Service Reactivated on provider', '2022-08-04 08:56:34', 'Activated Service', 9),
(513, 4753, 'Service Reactivated on provider', '2022-08-04 08:56:34', 'Activated Service', 9),
(514, 4752, 'Service Reactivated on provider', '2022-08-04 08:56:34', 'Activated Service', 9),
(515, 4752, 'Service Reactivated on provider', '2022-08-04 08:56:36', 'Activated Service', 9),
(516, 4753, 'Service Reactivated on provider', '2022-08-04 08:56:37', 'Activated Service', 9),
(517, 4752, 'Service Reactivated on provider', '2022-08-04 08:56:43', 'Activated Service', 9),
(518, 4752, 'Service Reactivated on provider', '2022-08-04 08:56:43', 'Activated Service', 9),
(519, 4750, 'Service Reactivated on provider', '2022-08-04 08:56:50', 'Activated Service', 9),
(520, 4752, 'Service Reactivated on provider', '2022-08-04 08:56:50', 'Activated Service', 9),
(521, 4750, 'Service Reactivated on provider', '2022-08-04 08:56:50', 'Activated Service', 9),
(522, 4750, 'Service Reactivated on provider', '2022-08-04 08:57:01', 'Activated Service', 9),
(523, 4744, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(524, 4746, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(525, 4751, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(526, 4748, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(527, 4750, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(528, 4752, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(529, 4743, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 5),
(530, 4744, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(531, 4745, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(532, 4747, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(533, 4745, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(534, 4746, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(535, 4748, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(536, 4750, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(537, 4750, 'Service Reactivated on provider', '2022-08-04 08:57:23', 'Activated Service', 9),
(538, 4750, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(539, 4751, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(540, 4753, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(541, 4743, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 5);
INSERT INTO `sync_logs` (`id`, `service_id`, `action`, `date`, `description`, `api_id`) VALUES
(542, 4744, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(543, 4746, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(544, 4747, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(545, 4749, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(546, 4750, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(547, 4751, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(548, 4752, 'Service Removed on provider', '2022-08-04 08:57:23', 'Deactivated Service', 9),
(549, 4752, 'Service Reactivated on provider', '2022-08-04 08:57:40', 'Activated Service', 9),
(550, 4752, 'Service Removed on provider', '2022-08-04 08:57:40', 'Deactivated Service', 9),
(551, 4753, 'Service Removed on provider', '2022-08-04 08:57:40', 'Deactivated Service', 9),
(552, 4753, 'Service Reactivated on provider', '2022-08-04 08:57:40', 'Activated Service', 9),
(553, 4752, 'Service Reactivated on provider', '2022-08-04 08:57:40', 'Activated Service', 9),
(554, 4752, 'Service Reactivated on provider', '2022-08-04 08:57:40', 'Activated Service', 9),
(555, 4753, 'Service Reactivated on provider', '2022-08-04 08:57:40', 'Activated Service', 9),
(556, 4753, 'Service Reactivated on provider', '2022-08-04 08:57:40', 'Activated Service', 9),
(557, 4747, 'Service Removed on provider', '2022-08-04 08:57:40', 'Deactivated Service', 9),
(558, 4743, 'Service Removed on provider', '2022-08-04 08:57:40', 'Deactivated Service', 5),
(559, 4746, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(560, 4743, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 5),
(561, 4743, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 5),
(562, 4747, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(563, 4747, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(564, 4751, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(565, 4743, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 5),
(566, 4744, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(567, 4744, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(568, 4747, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(569, 4745, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(570, 4750, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(571, 4746, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(572, 4746, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(573, 4750, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(574, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(575, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(576, 4748, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(577, 4748, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(578, 4750, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(579, 4749, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(580, 4753, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(581, 4750, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(582, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(583, 4745, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(584, 4751, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(585, 4752, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(586, 4749, 'Service Removed on provider', '2022-08-04 09:28:04', 'Deactivated Service', 9),
(587, 4753, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(588, 4750, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(589, 4752, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(590, 4750, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(591, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:04', 'Activated Service', 9),
(592, 4753, 'Service Reactivated on provider', '2022-08-04 09:28:08', 'Activated Service', 9),
(593, 4753, 'Service Reactivated on provider', '2022-08-04 09:28:14', 'Activated Service', 9),
(594, 4753, 'Service Reactivated on provider', '2022-08-04 09:28:14', 'Activated Service', 9),
(595, 4753, 'Service Reactivated on provider', '2022-08-04 09:28:14', 'Activated Service', 9),
(596, 4753, 'Service Reactivated on provider', '2022-08-04 09:28:14', 'Activated Service', 9),
(597, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:22', 'Activated Service', 9),
(598, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:22', 'Activated Service', 9),
(599, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:22', 'Activated Service', 9),
(600, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:22', 'Activated Service', 9),
(601, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:26', 'Activated Service', 9),
(602, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:29', 'Activated Service', 9),
(603, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:29', 'Activated Service', 9),
(604, 4751, 'Service Reactivated on provider', '2022-08-04 09:28:29', 'Activated Service', 9),
(605, 4746, 'Service Reactivated on provider', '2022-08-04 09:28:41', 'Activated Service', 9),
(606, 4746, 'Service Reactivated on provider', '2022-08-04 09:28:41', 'Activated Service', 9),
(607, 4746, 'Service Reactivated on provider', '2022-08-04 09:28:41', 'Activated Service', 9),
(608, 4746, 'Service Reactivated on provider', '2022-08-04 09:28:41', 'Activated Service', 9),
(609, 4746, 'Service Reactivated on provider', '2022-08-04 09:28:44', 'Activated Service', 9),
(610, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(611, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(612, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(613, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(614, 4753, 'Service Removed on provider', '2022-08-04 09:29:02', 'Deactivated Service', 9),
(615, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(616, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(617, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(618, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:02', 'Activated Service', 9),
(619, 4746, 'Service Reactivated on provider', '2022-08-04 09:29:04', 'Activated Service', 9),
(620, 4745, 'Service Removed on provider', '2022-08-04 09:59:30', 'Deactivated Service', 9),
(621, 4748, 'Service Removed on provider', '2022-08-04 09:59:30', 'Deactivated Service', 9),
(622, 4743, 'Service Removed on provider', '2022-08-04 09:59:30', 'Deactivated Service', 5),
(623, 4746, 'Service Removed on provider', '2022-08-04 09:59:30', 'Deactivated Service', 9),
(624, 4747, 'Service Removed on provider', '2022-08-04 09:59:30', 'Deactivated Service', 9),
(625, 4750, 'Service Removed on provider', '2022-08-04 09:59:30', 'Deactivated Service', 9),
(626, 4745, 'Service Removed on provider', '2022-08-04 09:59:30', 'Deactivated Service', 9),
(627, 4753, 'Service Reactivated on provider', '2022-08-04 09:59:35', 'Activated Service', 9),
(628, 4753, 'Service Reactivated on provider', '2022-08-04 09:59:35', 'Activated Service', 9),
(629, 4750, 'Service Reactivated on provider', '2022-08-04 09:59:43', 'Activated Service', 9),
(630, 4750, 'Service Reactivated on provider', '2022-08-04 09:59:43', 'Activated Service', 9),
(631, 4750, 'Service Reactivated on provider', '2022-08-04 09:59:46', 'Activated Service', 9),
(632, 4748, 'Service Reactivated on provider', '2022-08-04 09:59:46', 'Activated Service', 9),
(633, 4747, 'Service Reactivated on provider', '2022-08-04 09:59:47', 'Activated Service', 9),
(634, 4747, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(635, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(636, 4748, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(637, 4747, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(638, 4747, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(639, 4748, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(640, 4748, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(641, 4748, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(642, 4750, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(643, 4745, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(644, 4748, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(645, 4750, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(646, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(647, 4750, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(648, 4750, 'Service Reactivated on provider', '2022-08-04 10:00:02', 'Activated Service', 9),
(649, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:04', 'Activated Service', 9),
(650, 4748, 'Service Reactivated on provider', '2022-08-04 10:00:04', 'Activated Service', 9),
(651, 4747, 'Service Reactivated on provider', '2022-08-04 10:00:04', 'Activated Service', 9),
(652, 4747, 'Service Reactivated on provider', '2022-08-04 10:00:04', 'Activated Service', 9),
(653, 4745, 'Service Reactivated on provider', '2022-08-04 10:00:23', 'Activated Service', 9),
(654, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:23', 'Activated Service', 9),
(655, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:23', 'Activated Service', 9),
(656, 4747, 'Service Removed on provider', '2022-08-04 10:00:23', 'Deactivated Service', 9),
(657, 4743, 'Service Removed on provider', '2022-08-04 10:00:23', 'Deactivated Service', 5),
(658, 4745, 'Service Removed on provider', '2022-08-04 10:00:23', 'Deactivated Service', 9),
(659, 4752, 'Service Removed on provider', '2022-08-04 10:00:23', 'Deactivated Service', 9),
(660, 4745, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(661, 4744, 'Service Removed on provider', '2022-08-04 10:00:24', 'Deactivated Service', 9),
(662, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(663, 4745, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(664, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(665, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(666, 4743, 'Service Removed on provider', '2022-08-04 10:00:24', 'Deactivated Service', 5),
(667, 4744, 'Service Removed on provider', '2022-08-04 10:00:24', 'Deactivated Service', 9),
(668, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(669, 4745, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(670, 4745, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(671, 4746, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(672, 4748, 'Service Reactivated on provider', '2022-08-04 10:00:24', 'Activated Service', 9),
(673, 4745, 'Service Removed on provider', '2022-08-04 10:00:32', 'Deactivated Service', 9),
(674, 4752, 'Service Reactivated on provider', '2022-08-04 10:00:32', 'Activated Service', 9),
(675, 4744, 'Service Removed on provider', '2022-08-04 10:00:32', 'Deactivated Service', 9),
(676, 4753, 'Service Removed on provider', '2022-08-04 10:00:32', 'Deactivated Service', 9),
(677, 4752, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(678, 4748, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(679, 4749, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(680, 4747, 'Service Reactivated on provider', '2022-08-04 10:30:45', 'Activated Service', 9),
(681, 4745, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(682, 4743, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 5),
(683, 4746, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(684, 4748, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(685, 4751, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(686, 4744, 'Service Reactivated on provider', '2022-08-04 10:30:45', 'Activated Service', 9),
(687, 4747, 'Service Reactivated on provider', '2022-08-04 10:30:45', 'Activated Service', 9),
(688, 4747, 'Service Reactivated on provider', '2022-08-04 10:30:45', 'Activated Service', 9),
(689, 4746, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(690, 4747, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(691, 4753, 'Service Removed on provider', '2022-08-04 10:30:45', 'Deactivated Service', 9),
(692, 4747, 'Service Reactivated on provider', '2022-08-04 10:30:45', 'Activated Service', 9),
(693, 4752, 'Service Reactivated on provider', '2022-08-04 10:30:45', 'Activated Service', 9),
(694, 4752, 'Service Reactivated on provider', '2022-08-04 10:30:45', 'Activated Service', 9),
(695, 4751, 'Service Reactivated on provider', '2022-08-04 10:30:54', 'Activated Service', 9),
(696, 4751, 'Service Reactivated on provider', '2022-08-04 10:30:54', 'Activated Service', 9),
(697, 4751, 'Service Reactivated on provider', '2022-08-04 10:30:54', 'Activated Service', 9),
(698, 4752, 'Service Reactivated on provider', '2022-08-04 10:30:54', 'Activated Service', 9),
(699, 4752, 'Service Reactivated on provider', '2022-08-04 10:30:54', 'Activated Service', 9),
(700, 4753, 'Service Reactivated on provider', '2022-08-04 10:30:54', 'Activated Service', 9),
(701, 4753, 'Service Reactivated on provider', '2022-08-04 10:30:54', 'Activated Service', 9),
(702, 4748, 'Service Reactivated on provider', '2022-08-04 10:31:02', 'Activated Service', 9),
(703, 4748, 'Service Reactivated on provider', '2022-08-04 10:31:02', 'Activated Service', 9),
(704, 4749, 'Service Reactivated on provider', '2022-08-04 10:31:02', 'Activated Service', 9),
(705, 4749, 'Service Reactivated on provider', '2022-08-04 10:31:02', 'Activated Service', 9),
(706, 4748, 'Service Reactivated on provider', '2022-08-04 10:31:03', 'Activated Service', 9),
(707, 4744, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(708, 4745, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(709, 4746, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(710, 4747, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(711, 4748, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(712, 4749, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(713, 4751, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(714, 4752, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(715, 4753, 'Service Removed on provider', '2022-08-04 10:31:04', 'Deactivated Service', 9),
(716, 4748, 'Service Reactivated on provider', '2022-08-04 10:31:06', 'Activated Service', 9),
(717, 4743, 'Service Removed on provider', '2022-08-04 10:31:06', 'Deactivated Service', 5),
(718, 4744, 'Service Removed on provider', '2022-08-04 10:31:06', 'Deactivated Service', 9),
(719, 4746, 'Service Removed on provider', '2022-08-04 10:31:06', 'Deactivated Service', 9),
(720, 4753, 'Service Reactivated on provider', '2022-08-04 10:31:06', 'Activated Service', 9),
(721, 4747, 'Service Removed on provider', '2022-08-04 10:31:08', 'Deactivated Service', 9),
(722, 4748, 'Service Removed on provider', '2022-08-04 10:31:08', 'Deactivated Service', 9),
(723, 4750, 'Service Removed on provider', '2022-08-04 10:31:08', 'Deactivated Service', 9),
(724, 4753, 'Service Removed on provider', '2022-08-04 10:31:08', 'Deactivated Service', 9),
(725, 4753, 'Service Reactivated on provider', '2022-08-04 10:31:08', 'Activated Service', 9),
(726, 4748, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(727, 4749, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(728, 4750, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(729, 4743, 'Service Removed on provider', '2022-08-04 10:31:23', 'Deactivated Service', 5),
(730, 4749, 'Service Removed on provider', '2022-08-04 10:31:23', 'Deactivated Service', 9),
(731, 4750, 'Service Removed on provider', '2022-08-04 10:31:23', 'Deactivated Service', 9),
(732, 4751, 'Service Removed on provider', '2022-08-04 10:31:23', 'Deactivated Service', 9),
(733, 4751, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(734, 4749, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(735, 4752, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(736, 4752, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(737, 4751, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(738, 4753, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(739, 4751, 'Service Reactivated on provider', '2022-08-04 10:31:23', 'Activated Service', 9),
(740, 4749, 'Service Reactivated on provider', '2022-08-04 10:31:24', 'Activated Service', 9),
(741, 4745, 'Service Removed on provider', '2022-08-04 10:31:24', 'Deactivated Service', 9),
(742, 4749, 'Service Removed on provider', '2022-08-04 10:31:24', 'Deactivated Service', 9),
(743, 4750, 'Service Removed on provider', '2022-08-04 10:31:24', 'Deactivated Service', 9),
(744, 4752, 'Service Removed on provider', '2022-08-04 10:31:24', 'Deactivated Service', 9),
(745, 4751, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(746, 4746, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(747, 4748, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(748, 4750, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(749, 4751, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(750, 4752, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(751, 4751, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(752, 4745, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(753, 4746, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(754, 4752, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(755, 4746, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(756, 4748, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(757, 4749, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(758, 4751, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(759, 4753, 'Service Removed on provider', '2022-08-04 10:31:40', 'Deactivated Service', 9),
(760, 4751, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(761, 4746, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(762, 4745, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(763, 4747, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(764, 4749, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(765, 4747, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(766, 4748, 'Service Reactivated on provider', '2022-08-04 10:31:40', 'Activated Service', 9),
(767, 4750, 'Service Reactivated on provider', '2022-08-04 10:31:45', 'Activated Service', 9),
(768, 4753, 'Service Reactivated on provider', '2022-08-04 10:31:45', 'Activated Service', 9),
(769, 4747, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(770, 4745, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(771, 4748, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(772, 4743, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 5),
(773, 4746, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(774, 4746, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(775, 4748, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(776, 4746, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(777, 4745, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(778, 4744, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(779, 4743, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 5),
(780, 4749, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(781, 4750, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(782, 4743, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 5),
(783, 4748, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(784, 4749, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(785, 4751, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(786, 4744, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(787, 4752, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(788, 4750, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(789, 4749, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(790, 4745, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(791, 4744, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(792, 4752, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(793, 4753, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(794, 4744, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(795, 4746, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(796, 4747, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(797, 4752, 'Service Removed on provider', '2022-08-04 11:01:50', 'Deactivated Service', 9),
(798, 4745, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(799, 4752, 'Service Reactivated on provider', '2022-08-04 11:01:50', 'Activated Service', 9),
(800, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:23', 'Activated Service', 9),
(801, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:23', 'Activated Service', 9),
(802, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:23', 'Activated Service', 9),
(803, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:23', 'Activated Service', 9),
(804, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:23', 'Activated Service', 9),
(805, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:23', 'Activated Service', 9),
(806, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:23', 'Activated Service', 9),
(807, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:24', 'Activated Service', 9),
(808, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(809, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(810, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(811, 4744, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(812, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(813, 4746, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(814, 4744, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(815, 4750, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(816, 4746, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(817, 4751, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(818, 4750, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(819, 4752, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(820, 4751, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(821, 4753, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(822, 4752, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(823, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(824, 4753, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(825, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(826, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(827, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(828, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(829, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(830, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(831, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(832, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(833, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(834, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(835, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(836, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(837, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(838, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(839, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(840, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(841, 4745, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(842, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(843, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(844, 4745, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(845, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(846, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(847, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(848, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(849, 4746, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(850, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(851, 4745, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(852, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(853, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(854, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(855, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(856, 4743, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 5),
(857, 4743, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 5),
(858, 4747, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(859, 4747, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(860, 4749, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(861, 4749, 'Service Removed on provider', '2022-08-04 11:02:44', 'Deactivated Service', 9),
(862, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(863, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(864, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(865, 4747, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(866, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(867, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(868, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(869, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(870, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(871, 4748, 'Service Reactivated on provider', '2022-08-04 11:02:44', 'Activated Service', 9),
(872, 4747, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(873, 4749, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(874, 4747, 'Service Reactivated on provider', '2022-08-04 11:03:02', 'Activated Service', 9),
(875, 4750, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(876, 4745, 'Service Reactivated on provider', '2022-08-04 11:03:02', 'Activated Service', 9),
(877, 4747, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(878, 4744, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(879, 4748, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(880, 4749, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(881, 4751, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(882, 4752, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(883, 4751, 'Service Reactivated on provider', '2022-08-04 11:03:02', 'Activated Service', 9),
(884, 4753, 'Service Reactivated on provider', '2022-08-04 11:03:02', 'Activated Service', 9),
(885, 4746, 'Service Reactivated on provider', '2022-08-04 11:03:02', 'Activated Service', 9),
(886, 4752, 'Service Reactivated on provider', '2022-08-04 11:03:02', 'Activated Service', 9),
(887, 4745, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(888, 4747, 'Service Removed on provider', '2022-08-04 11:03:02', 'Deactivated Service', 9),
(889, 4746, 'Service Reactivated on provider', '2022-08-04 11:03:03', 'Activated Service', 9),
(890, 4746, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(891, 4749, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(892, 4751, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(893, 4743, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 5),
(894, 4747, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(895, 4747, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(896, 4748, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(897, 4749, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(898, 4748, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(899, 4747, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(900, 4753, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(901, 4751, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(902, 4743, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 5),
(903, 4748, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(904, 4752, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(905, 4745, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(906, 4751, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(907, 4743, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 5),
(908, 4749, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(909, 4751, 'Service Removed on provider', '2022-08-04 11:04:03', 'Deactivated Service', 9),
(910, 4751, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(911, 4752, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(912, 4745, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(913, 4745, 'Service Reactivated on provider', '2022-08-04 11:04:03', 'Activated Service', 9),
(914, 4746, 'Service Reactivated on provider', '2022-08-04 11:05:06', 'Activated Service', 9),
(915, 4749, 'Service Reactivated on provider', '2022-08-04 11:05:06', 'Activated Service', 9),
(916, 4751, 'Service Reactivated on provider', '2022-08-04 11:05:06', 'Activated Service', 9),
(917, 4752, 'Service Reactivated on provider', '2022-08-04 11:06:03', 'Activated Service', 9),
(918, 4745, 'Service Removed on provider', '2022-08-04 11:07:03', 'Deactivated Service', 9),
(919, 4748, 'Service Removed on provider', '2022-08-04 11:07:03', 'Deactivated Service', 9),
(920, 4752, 'Service Removed on provider', '2022-08-04 11:08:02', 'Deactivated Service', 9),
(921, 4745, 'Service Reactivated on provider', '2022-08-04 11:08:02', 'Activated Service', 9),
(922, 4753, 'Service Reactivated on provider', '2022-08-04 11:08:02', 'Activated Service', 9),
(923, 4749, 'Service Removed on provider', '2022-08-04 11:38:28', 'Deactivated Service', 9),
(924, 4748, 'Service Reactivated on provider', '2022-08-04 11:38:28', 'Activated Service', 9),
(925, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(926, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(927, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(928, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(929, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(930, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(931, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(932, 4752, 'Service Reactivated on provider', '2022-08-04 11:38:42', 'Activated Service', 9),
(933, 4749, 'Service Reactivated on provider', '2022-08-04 11:38:47', 'Activated Service', 9),
(934, 4749, 'Service Reactivated on provider', '2022-08-04 11:38:47', 'Activated Service', 9),
(935, 4749, 'Service Reactivated on provider', '2022-08-04 11:38:47', 'Activated Service', 9),
(936, 4749, 'Service Reactivated on provider', '2022-08-04 11:38:47', 'Activated Service', 9),
(937, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(938, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(939, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(940, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(941, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(942, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(943, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(944, 4749, 'Service Reactivated on provider', '2022-08-04 11:39:02', 'Activated Service', 9),
(945, 4754, 'Price Changed on\r\nprovider from 1728.01 to 3109.55', '2022-08-04 16:29:21', 'Price changed from 10 to 17.994976880921', 9),
(946, 4754, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:20', 'Price changed from 17.99 to 29.991471466932', 9),
(947, 4754, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:20', 'Price changed from 29.99 to 49.99689990513', 9),
(948, 4754, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:20', 'Price changed from 50.00 to 83.355951825827', 9),
(949, 4755, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:23', 'Price changed from 10 to 16.671190365166', 9),
(950, 4756, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:23', 'Price changed from 10 to 16.671190365166', 9),
(951, 4756, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:23', 'Price changed from 16.67 to 27.790874338732', 9),
(952, 4756, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:23', 'Price changed from 27.79 to 46.329238024795', 9),
(953, 4755, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:23', 'Price changed from 16.67 to 27.790874338732', 9),
(954, 4755, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:23', 'Price changed from 27.79 to 46.329238024795', 9),
(955, 4755, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:23', 'Price changed from 46.33 to 77.237624961812', 9),
(956, 4756, 'Price Changed on\r\nprovider from 3109.55 to 5183.99', '2022-08-04 17:01:24', 'Price changed from 46.33 to 77.237624961812', 9),
(957, 4756, 'Price Changed on\r\nprovider from 5183.99 to 1727.36', '2022-08-04 17:04:02', 'Price changed from 77.24 to 25.737180511537', 9),
(958, 4755, 'Price Changed on\r\nprovider from 5183.99 to 1727.36', '2022-08-04 17:04:02', 'Price changed from 77.24 to 25.737180511537', 9),
(959, 4754, 'Price Changed on\r\nprovider from 5183.99 to 1727.36', '2022-08-04 17:04:02', 'Price changed from 83.36 to 27.776428889716', 9),
(960, 4762, 'Price Changed on\r\nprovider from 220.21 to 660.78', '2022-08-04 17:37:23', 'Price changed from 220.21 to 660.78', 9),
(961, 4762, 'Price Changed on\r\nprovider from 220.21 to 660.78', '2022-08-04 17:37:23', 'Price changed from 660.78 to 1982.7901021752', 9),
(962, 4762, 'Price Changed on\r\nprovider from 220.21 to 660.78', '2022-08-04 17:37:23', 'Price changed from 1982.79 to 5949.7206130512', 9),
(963, 4762, 'Price Changed on\r\nprovider from 220.21 to 660.78', '2022-08-04 17:37:23', 'Price changed from 5949.72 to 17853.21275873', 9),
(964, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:25', 'Price changed from 259.08 to 777.4', 9),
(965, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:25', 'Price changed from 777.40 to 2332.6800988112', 9),
(966, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:26', 'Price changed from 410.20 to 1230.86', 9),
(967, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:26', 'Price changed from 2332.68 to 6999.4805928671', 9),
(968, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:37:39', 'Price changed from 159.76 to 479.4', 9),
(969, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:39', 'Price changed from 1230.86 to 3693.3601647977', 9),
(970, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:39', 'Price changed from 3693.36 to 11082.420988786', 9),
(971, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:37:39', 'Price changed from 181.35 to 544.18', 9),
(972, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:39', 'Price changed from 6999.48 to 21002.762667902', 9),
(973, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:37:39', 'Price changed from 544.18 to 1632.93009319', 9),
(974, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:37:39', 'Price changed from 1632.93 to 4899.9605591398', 9),
(975, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:39', 'Price changed from 21002.76 to 63021.250671607', 9),
(976, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:39', 'Price changed from 63021.25 to 189102.6700247', 9),
(977, 4762, 'Price Changed on\r\nprovider from 220.21 to 660.78', '2022-08-04 17:37:40', 'Price changed from 17853.21 to 53571.791034921', 9),
(978, 4762, 'Price Changed on\r\nprovider from 220.21 to 660.78', '2022-08-04 17:37:40', 'Price changed from 53571.79 to 160751.86138777', 9),
(979, 4762, 'Price Changed on\r\nprovider from 220.21 to 660.78', '2022-08-04 17:37:40', 'Price changed from 160751.86 to 482365.07901912', 9),
(980, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:40', 'Price changed from 11082.42 to 33254.284449537', 9),
(981, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:40', 'Price changed from 33254.28 to 99783.917798147', 9),
(982, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:40', 'Price changed from 189102.67 to 567424.79410993', 9),
(983, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:40', 'Price changed from 99783.92 to 299415.00675573', 9),
(984, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:37:44', 'Price changed from 479.40 to 1438.5600901352', 9),
(985, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:37:44', 'Price changed from 1438.56 to 4316.7605408112', 9),
(986, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:44', 'Price changed from 299415.01 to 898434.81035739', 9),
(987, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:37:44', 'Price changed from 4899.96 to 14703.392516129', 9),
(988, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:37:44', 'Price changed from 4316.76 to 12953.52243365', 9),
(989, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:37:56', 'Price changed from 12953.52 to 38870.289734602', 9),
(990, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:37:56', 'Price changed from 38870.29 to 116640.06651227', 9),
(991, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:56', 'Price changed from 898434.81 to 2695873.8913618', 9),
(992, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:37:56', 'Price changed from 14703.39 to 44120.710064516', 9),
(993, 4761, 'Price Changed on\r\nprovider from 410.20 to 1230.86', '2022-08-04 17:37:56', 'Price changed from 2695873.89 to 8089330.4150302', 9),
(994, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:37:56', 'Price changed from 44120.71 to 132393.7577491', 9),
(995, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:37:56', 'Price changed from 132393.76 to 397276.18592115', 9),
(996, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:56', 'Price changed from 567424.79 to 1702624.7944496', 9),
(997, 4760, 'Price Changed on\r\nprovider from 259.08 to 777.40', '2022-08-04 17:37:56', 'Price changed from 1702624.79 to 5108925.8597576', 9),
(998, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:38:04', 'Price changed from 116640.07 to 350007.8214697', 9),
(999, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:39:04', 'Price changed from 350007.82 to 1050286.3602153', 9),
(1000, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:39:04', 'Price changed from 1050286.36 to 3151647.9781172', 9),
(1001, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:39:04', 'Price changed from 397276.19 to 1192113.3557993', 9),
(1002, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:39:04', 'Price changed from 1192113.36 to 3577194.6415484', 9),
(1003, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:39:04', 'Price changed from 3151647.98 to 9457311.2269154', 9),
(1004, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:39:04', 'Price changed from 3577194.64 to 10734148.217233', 9),
(1005, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:39:04', 'Price changed from 9457311.23 to 28379037.328881', 9),
(1006, 4759, 'Price Changed on\r\nprovider from 159.76 to 479.40', '2022-08-04 17:39:04', 'Price changed from 28379037.33 to 85158428.242376', 9),
(1007, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:39:04', 'Price changed from 10734148.22 to 32210139.389907', 9),
(1008, 4758, 'Price Changed on\r\nprovider from 181.35 to 544.18', '2022-08-04 17:39:04', 'Price changed from 32210139.39 to 96653507.875656', 9),
(1009, 4830, 'Price Changed on\r\nprovider from 1723.70 to 5171.08', '2022-08-04 18:14:15', 'Price changed from 10 to 29.999883970529', 9),
(1010, 4830, 'Price Changed on\r\nprovider from 1723.70 to 5171.08', '2022-08-04 18:14:20', 'Price changed from 30.00 to 89.999651911585', 9),
(1011, 4830, 'Price Changed on\r\nprovider from 1723.70 to 5171.08', '2022-08-04 18:14:20', 'Price changed from 90.00 to 269.99895573476', 9),
(1012, 4830, 'Price Changed on\r\nprovider from 5171.08 to 1725.13', '2022-08-04 18:51:35', 'Price changed from 270.00 to 90.075013343441', 9),
(1013, 4830, 'Service Removed on provider', '2022-08-05 19:10:32', 'Deactivated Service', 9);

-- --------------------------------------------------------

--
-- Table structure for table `themes`
--

CREATE TABLE `themes` (
  `id` int(11) NOT NULL,
  `theme_name` text NOT NULL,
  `theme_dirname` text NOT NULL,
  `theme_extras` text NOT NULL,
  `last_modified` datetime NOT NULL,
  `newpage` text NOT NULL,
  `colour` enum('1','2') NOT NULL DEFAULT '1',
  `site_theme_alt` text NOT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `themes`
--

INSERT INTO `themes` (`id`, `theme_name`, `theme_dirname`, `theme_extras`, `last_modified`, `newpage`, `colour`, `site_theme_alt`) VALUES
(313, 'THEME', 'salzemedia', '<div class=\"p-3 rounded bg-pattern text-white h-100\" style=\"background-image: url(https://wallpapercave.com/uwp/uwp3455314.jpeg);\r\n    background-size: cover;\">\r\n               <div class=\"d-flex justify-content-between align-items-center\">\r\n                  <div class=\"ulevel-c bar-25\">\r\n                     <div class=\"ulevel-text\">\r\n                        <i class=\"ri-shield-user-line\"></i>\r\n                     </div>\r\n                  </div>', '2022-12-27 09:05:52', '{% include \'header.twig\' %}\r\n	<br><br><br>\r\n	\r\n	<div class=\"container-fluid container-fluid-spacious\">\r\n		<div class=\"row\">\r\n			<div class=\"col-md-12\">\r\n			{% if contentText %}\r\n{{ contentText }}\r\n{% endif %}\r\n				{% if contentText2 %}\r\n{{ contentText2 }}\r\n{% endif %}\r\n				\r\n			</div>\r\n		</div>\r\n	</div>\r\n   \r\n      \r\n        \r\n   ', '2', '<div class=\"p-3 rounded bg-pattern text-white h-100\" style=\"background-image: url(https://wallpapercave.com/uwp/uwp3455314.jpeg);     background-size: cover;\">                <div class=\"d-flex justify-content-between align-items-center\">                   <div class=\"ulevel-c bar-25\">                      <div class=\"ulevel-text\">                         <i class=\"ri-shield-user-line\"></i>                      </div>                   </div>');

-- --------------------------------------------------------

--
-- Table structure for table `tickets`
--

CREATE TABLE `tickets` (
  `ticket_id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `subject` varchar(225) NOT NULL,
  `time` datetime NOT NULL,
  `lastupdate_time` datetime NOT NULL,
  `client_new` enum('1','2') NOT NULL DEFAULT '2',
  `status` enum('pending','answered','closed') NOT NULL DEFAULT 'pending',
  `support_new` enum('1','2') NOT NULL DEFAULT '1',
  `canmessage` enum('1','2') NOT NULL DEFAULT '2'
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

-- --------------------------------------------------------

--
-- Table structure for table `ticket_reply`
--

CREATE TABLE `ticket_reply` (
  `id` int(11) NOT NULL,
  `ticket_id` int(11) NOT NULL,
  `client_id` int(11) NOT NULL,
  `time` datetime NOT NULL,
  `support` enum('1','2') NOT NULL DEFAULT '1',
  `message` text CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  `readed` enum('1','2') NOT NULL DEFAULT '1'
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `ticket_reply`
--

INSERT INTO `ticket_reply` (`id`, `ticket_id`, `client_id`, `time`, `support`, `message`, `readed`) VALUES
(1, 1, 0, '2022-04-24 18:26:55', '1', 'dfdsfsdfsdfsdf', '1'),
(2, 1, 0, '2022-04-24 20:29:18', '2', 'يبسيبسيبيب', '1'),
(3, 1, 0, '2022-04-24 20:29:29', '1', 'سيبسيبسيب', '1'),
(4, 2, 0, '2022-04-26 01:48:34', '1', 'سيبسيبسيبسيبسيب', '1'),
(5, 2, 0, '2022-04-26 01:51:04', '2', 'asdasdasd', '1'),
(6, 2, 0, '2022-04-26 03:30:50', '1', 'dfgdfgdfgdfg', '1'),
(7, 2, 0, '2022-04-26 03:30:55', '1', 'fgdfgdfgdfg', '1'),
(8, 2, 0, '2022-04-26 03:31:32', '1', 'dfgdfgdfg', '1'),
(9, 2, 0, '2022-04-26 03:32:38', '1', 'fgdfgdfg', '1'),
(10, 3, 0, '2022-04-26 14:49:38', '1', 'اريد طريقة دفع', '1'),
(11, 3, 0, '2022-04-27 16:23:42', '2', 'hi gfgfgfgfg', '1'),
(12, 4, 0, '2022-04-27 17:50:25', '1', 'asdasdasdasdasdasd', '1'),
(13, 4, 0, '2022-04-27 17:50:39', '2', 'asdasdasdasd', '1'),
(14, 4, 0, '2022-04-27 17:56:06', '1', 'sdfsdfsdfsdf', '1'),
(15, 4, 0, '2022-04-27 17:56:17', '2', 'asdasdasdasd', '1'),
(16, 5, 0, '2022-04-27 18:33:19', '1', 'adasdasdasdsd', '1'),
(17, 5, 0, '2022-04-27 18:33:29', '2', 'asdasdasd', '1'),
(18, 5, 0, '2022-04-27 18:34:37', '2', 'asdasdasdasdasd', '1'),
(19, 5, 0, '2022-04-27 18:35:38', '1', 'sdfsdfsdfsdf', '1'),
(20, 5, 0, '2022-04-27 18:35:57', '2', 'sadasdasdasd', '1'),
(21, 6, 0, '2022-04-28 14:47:13', '1', 'hi', '1'),
(22, 6, 0, '2022-04-28 14:47:13', '2', 'You will be answered within minutes', '1'),
(23, 7, 0, '2022-04-28 16:41:52', '1', 'vxcvxcvxcv', '1'),
(24, 6, 0, '2022-04-28 16:45:04', '1', 'asdasdsadsd', '1'),
(25, 8, 0, '2022-05-06 16:04:16', '1', 'hi\r\n', '1'),
(26, 8, 0, '2022-05-06 16:07:57', '2', 'hi2', '1'),
(27, 8, 0, '2022-05-06 16:47:52', '1', 'dasdasd', '1'),
(28, 8, 0, '2022-05-06 16:48:50', '1', 'sdfsdfsdf', '1'),
(29, 8, 0, '2022-05-06 17:06:36', '1', 'dfsdfsdf', '1'),
(30, 8, 0, '2022-05-06 17:06:45', '1', 'sdfsdfsdf', '1'),
(31, 8, 0, '2022-05-06 17:08:12', '1', 'zdfsfsdf', '1'),
(32, 8, 0, '2022-05-06 17:08:14', '1', 'sdfsdfs', '1'),
(33, 8, 0, '2022-05-06 17:08:16', '1', 'sdfsdfsdf', '1'),
(34, 8, 0, '2022-05-06 17:08:18', '1', 'sdfdsf', '1'),
(35, 8, 0, '2022-05-06 17:08:20', '1', 'sdfsdf', '1'),
(36, 8, 0, '2022-05-06 17:08:22', '1', 'sdfsdf', '1'),
(37, 8, 0, '2022-05-06 17:08:24', '1', 'sdfsdf', '1'),
(38, 8, 0, '2022-05-06 17:08:26', '1', 'sdfsdf', '1'),
(39, 8, 0, '2022-05-06 17:08:29', '1', 'sdfsdf', '1'),
(40, 8, 0, '2022-05-06 17:08:32', '1', 'sdfsdf', '1'),
(41, 8, 0, '2022-05-06 20:28:10', '1', 'fdsfsdf', '1');

-- --------------------------------------------------------

--
-- Table structure for table `ticket_subjects`
--

CREATE TABLE `ticket_subjects` (
  `subject_id` int(11) NOT NULL,
  `subject` varchar(225) NOT NULL,
  `content` text DEFAULT NULL,
  `auto_reply` enum('0','1') NOT NULL DEFAULT '0'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci ROW_FORMAT=COMPACT;

--
-- Dumping data for table `ticket_subjects`
--

INSERT INTO `ticket_subjects` (`subject_id`, `subject`, `content`, `auto_reply`) VALUES
(1, 'Order', '', '0'),
(2, 'Payment', '', '0'),
(4, 'Complaint & Suggestion', '', '0'),
(6, 'Others', 'You will be answered within minutes', '1'),
(7, 'Request Service', '', '0');

-- --------------------------------------------------------

--
-- Table structure for table `units_per_page`
--

CREATE TABLE `units_per_page` (
  `id` int(11) NOT NULL,
  `unit` int(11) NOT NULL,
  `page` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Dumping data for table `units_per_page`
--

INSERT INTO `units_per_page` (`id`, `unit`, `page`) VALUES
(1, 50, 'clients'),
(2, 50, 'orders'),
(3, 50, 'payments'),
(4, 50, 'refill'),
(5, 50, 'bulk');

-- --------------------------------------------------------

--
-- Table structure for table `updates`
--

CREATE TABLE `updates` (
  `u_id` int(11) NOT NULL,
  `service_id` int(11) NOT NULL,
  `action` varchar(225) NOT NULL,
  `date` datetime NOT NULL,
  `description` varchar(225) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL DEFAULT 'Not enough data'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

--
-- Indexes for dumped tables
--

--
-- Indexes for table `admins`
--
ALTER TABLE `admins`
  ADD PRIMARY KEY (`admin_id`);

--
-- Indexes for table `article`
--
ALTER TABLE `article`
  ADD PRIMARY KEY (`id`),
  ADD KEY `title` (`title`);

--
-- Indexes for table `bank_accounts`
--
ALTER TABLE `bank_accounts`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `blogs`
--
ALTER TABLE `blogs`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `bulkedit`
--
ALTER TABLE `bulkedit`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `categories`
--
ALTER TABLE `categories`
  ADD PRIMARY KEY (`category_id`);

--
-- Indexes for table `childpanels`
--
ALTER TABLE `childpanels`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `clients`
--
ALTER TABLE `clients`
  ADD PRIMARY KEY (`client_id`);

--
-- Indexes for table `clients_category`
--
ALTER TABLE `clients_category`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `clients_price`
--
ALTER TABLE `clients_price`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `clients_service`
--
ALTER TABLE `clients_service`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `client_report`
--
ALTER TABLE `client_report`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `currency`
--
ALTER TABLE `currency`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `earn`
--
ALTER TABLE `earn`
  ADD PRIMARY KEY (`earn_id`);

--
-- Indexes for table `files`
--
ALTER TABLE `files`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `General_options`
--
ALTER TABLE `General_options`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `integrations`
--
ALTER TABLE `integrations`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `kuponlar`
--
ALTER TABLE `kuponlar`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `kupon_kullananlar`
--
ALTER TABLE `kupon_kullananlar`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `languages`
--
ALTER TABLE `languages`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `Mailforms`
--
ALTER TABLE `Mailforms`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `menus`
--
ALTER TABLE `menus`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `news`
--
ALTER TABLE `news`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `notifications_popup`
--
ALTER TABLE `notifications_popup`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `orders`
--
ALTER TABLE `orders`
  ADD PRIMARY KEY (`order_id`) USING BTREE;

--
-- Indexes for table `pages`
--
ALTER TABLE `pages`
  ADD PRIMARY KEY (`page_id`);

--
-- Indexes for table `panel_categories`
--
ALTER TABLE `panel_categories`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `panel_info`
--
ALTER TABLE `panel_info`
  ADD PRIMARY KEY (`panel_id`);

--
-- Indexes for table `payments`
--
ALTER TABLE `payments`
  ADD PRIMARY KEY (`payment_id`);

--
-- Indexes for table `payments_bonus`
--
ALTER TABLE `payments_bonus`
  ADD PRIMARY KEY (`bonus_id`);

--
-- Indexes for table `payment_methods`
--
ALTER TABLE `payment_methods`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `payment_methodsold`
--
ALTER TABLE `payment_methodsold`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `referral`
--
ALTER TABLE `referral`
  ADD PRIMARY KEY (`referral_id`);

--
-- Indexes for table `referral_payouts`
--
ALTER TABLE `referral_payouts`
  ADD PRIMARY KEY (`r_p_id`);

--
-- Indexes for table `refill_status`
--
ALTER TABLE `refill_status`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `serviceapi_alert`
--
ALTER TABLE `serviceapi_alert`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `services`
--
ALTER TABLE `services`
  ADD PRIMARY KEY (`service_id`);

--
-- Indexes for table `service_api`
--
ALTER TABLE `service_api`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `settings`
--
ALTER TABLE `settings`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `sync_logs`
--
ALTER TABLE `sync_logs`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `themes`
--
ALTER TABLE `themes`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `tickets`
--
ALTER TABLE `tickets`
  ADD PRIMARY KEY (`ticket_id`);

--
-- Indexes for table `ticket_reply`
--
ALTER TABLE `ticket_reply`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `ticket_subjects`
--
ALTER TABLE `ticket_subjects`
  ADD PRIMARY KEY (`subject_id`);

--
-- Indexes for table `units_per_page`
--
ALTER TABLE `units_per_page`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `updates`
--
ALTER TABLE `updates`
  ADD PRIMARY KEY (`u_id`);

--
-- AUTO_INCREMENT for dumped tables
--

--
-- AUTO_INCREMENT for table `admins`
--
ALTER TABLE `admins`
  MODIFY `admin_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT for table `article`
--
ALTER TABLE `article`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `bank_accounts`
--
ALTER TABLE `bank_accounts`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `blogs`
--
ALTER TABLE `blogs`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `bulkedit`
--
ALTER TABLE `bulkedit`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `categories`
--
ALTER TABLE `categories`
  MODIFY `category_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `childpanels`
--
ALTER TABLE `childpanels`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT for table `clients`
--
ALTER TABLE `clients`
  MODIFY `client_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `clients_category`
--
ALTER TABLE `clients_category`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `clients_price`
--
ALTER TABLE `clients_price`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `clients_service`
--
ALTER TABLE `clients_service`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `client_report`
--
ALTER TABLE `client_report`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=306;

--
-- AUTO_INCREMENT for table `currency`
--
ALTER TABLE `currency`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=9;

--
-- AUTO_INCREMENT for table `earn`
--
ALTER TABLE `earn`
  MODIFY `earn_id` int(255) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `files`
--
ALTER TABLE `files`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `General_options`
--
ALTER TABLE `General_options`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `integrations`
--
ALTER TABLE `integrations`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=15;

--
-- AUTO_INCREMENT for table `kuponlar`
--
ALTER TABLE `kuponlar`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `kupon_kullananlar`
--
ALTER TABLE `kupon_kullananlar`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `languages`
--
ALTER TABLE `languages`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT for table `Mailforms`
--
ALTER TABLE `Mailforms`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `menus`
--
ALTER TABLE `menus`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=50;

--
-- AUTO_INCREMENT for table `news`
--
ALTER TABLE `news`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT for table `notifications_popup`
--
ALTER TABLE `notifications_popup`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=19;

--
-- AUTO_INCREMENT for table `orders`
--
ALTER TABLE `orders`
  MODIFY `order_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=21;

--
-- AUTO_INCREMENT for table `pages`
--
ALTER TABLE `pages`
  MODIFY `page_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=908;

--
-- AUTO_INCREMENT for table `panel_categories`
--
ALTER TABLE `panel_categories`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `panel_info`
--
ALTER TABLE `panel_info`
  MODIFY `panel_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `payments`
--
ALTER TABLE `payments`
  MODIFY `payment_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=123;

--
-- AUTO_INCREMENT for table `payments_bonus`
--
ALTER TABLE `payments_bonus`
  MODIFY `bonus_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `payment_methods`
--
ALTER TABLE `payment_methods`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=988;

--
-- AUTO_INCREMENT for table `payment_methodsold`
--
ALTER TABLE `payment_methodsold`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=31;

--
-- AUTO_INCREMENT for table `referral`
--
ALTER TABLE `referral`
  MODIFY `referral_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=69;

--
-- AUTO_INCREMENT for table `referral_payouts`
--
ALTER TABLE `referral_payouts`
  MODIFY `r_p_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `refill_status`
--
ALTER TABLE `refill_status`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `serviceapi_alert`
--
ALTER TABLE `serviceapi_alert`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=968;

--
-- AUTO_INCREMENT for table `services`
--
ALTER TABLE `services`
  MODIFY `service_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `service_api`
--
ALTER TABLE `service_api`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `settings`
--
ALTER TABLE `settings`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `sync_logs`
--
ALTER TABLE `sync_logs`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=1014;

--
-- AUTO_INCREMENT for table `themes`
--
ALTER TABLE `themes`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=314;

--
-- AUTO_INCREMENT for table `tickets`
--
ALTER TABLE `tickets`
  MODIFY `ticket_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `ticket_reply`
--
ALTER TABLE `ticket_reply`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=42;

--
-- AUTO_INCREMENT for table `ticket_subjects`
--
ALTER TABLE `ticket_subjects`
  MODIFY `subject_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=8;

--
-- AUTO_INCREMENT for table `units_per_page`
--
ALTER TABLE `units_per_page`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT for table `updates`
--
ALTER TABLE `updates`
  MODIFY `u_id` int(11) NOT NULL AUTO_INCREMENT;
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
