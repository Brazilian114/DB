--
-- Database: `carcare`
--

-- --------------------------------------------------------

--
-- Table structure for table `booking`
--

CREATE TABLE `booking` (
  `booking_id` int(10) NOT NULL,
  `user_id_fk` int(10) NOT NULL,
  `username` varchar(20) NOT NULL,
  `license` text NOT NULL,
  `province` varchar(20) NOT NULL,
  `datetime` text NOT NULL,
  `tel` text NOT NULL,
  `status` varchar(10) NOT NULL,
  `booking_service_id` int(10) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- --------------------------------------------------------

--
-- Table structure for table `booking_service`
--

CREATE TABLE `booking_service` (
  `booking_service_id` int(10) NOT NULL,
  `service_name` varchar(10) NOT NULL,
  `service_price` varchar(10) NOT NULL,
  `service_time` time NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Dumping data for table `booking_service`
--

INSERT INTO `booking_service` (`booking_service_id`, `service_name`, `service_price`, `service_time`) VALUES
(1, 'ล้าง  อัด ', '100', '00:45:00'),
(2, 'ล้างห้องเค', '50', '00:15:00'),
(3, 'ดูดฝุ่น', '50', '00:15:00'),
(4, 'เคลือบยาง', '50', '00:30:00');

-- --------------------------------------------------------

--
-- Table structure for table `booking_time`
--

CREATE TABLE `booking_time` (
  `time` varchar(8) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Dumping data for table `booking_time`
--

INSERT INTO `booking_time` (`time`) VALUES
('10:00:00'),
('11:00:00'),
('12:00:00'),
('13:00:00'),
('14:00:00'),
('15:00:00'),
('16:00:00'),
('17:00:00'),
('18:00:00'),
('19:00:00');

-- --------------------------------------------------------

--
-- Table structure for table `customer`
--

CREATE TABLE `customer` (
  `user_id` int(10) NOT NULL,
  `email` varchar(200) NOT NULL,
  `username` varchar(300) NOT NULL,
  `license` varchar(200) NOT NULL,
  `province` text NOT NULL,
  `tel` varchar(200) NOT NULL,
  `password` varchar(300) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Indexes for dumped tables
--

--
-- Indexes for table `booking`
--
ALTER TABLE `booking`
  ADD PRIMARY KEY (`booking_id`),
  ADD KEY `user_id_fk` (`user_id_fk`),
  ADD KEY `booking_service_fk` (`booking_service_id`);

--
-- Indexes for table `booking_service`
--
ALTER TABLE `booking_service`
  ADD PRIMARY KEY (`booking_service_id`);

--
-- Indexes for table `customer`
--
ALTER TABLE `customer`
  ADD PRIMARY KEY (`user_id`);

--
-- AUTO_INCREMENT for dumped tables
--

--
-- AUTO_INCREMENT for table `booking`
--
ALTER TABLE `booking`
  MODIFY `booking_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=41;

--
-- AUTO_INCREMENT for table `booking_service`
--
ALTER TABLE `booking_service`
  MODIFY `booking_service_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT for table `customer`
--
ALTER TABLE `customer`
  MODIFY `user_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=56;

--
-- Constraints for dumped tables
--

--
-- Constraints for table `booking`
--
ALTER TABLE `booking`
  ADD CONSTRAINT `booking_ibfk_2` FOREIGN KEY (`user_id_fk`) REFERENCES `customer` (`user_id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
