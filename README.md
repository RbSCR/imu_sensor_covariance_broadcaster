# imu_sensor_covariance_broadcaster

![Project Status](https://img.shields.io/badge/Status-Work%20in%20progress-orange)
![ROS 2](https://img.shields.io/badge/ROS%202-Jazzy%20|%20Kilted%20(Ubuntu%2024.04)-blue?style=flat&logo=ros&logoSize=auto)
![C++](https://img.shields.io/badge/C++-17-blue?style=flat&logo=cplusplus&logoColor=white)
![License](https://img.shields.io/github/license/rbscr/bno08x_rand?label=License)
[![ROS 2 Builder](https://github.com/RbSCR/imu_sensor_covariance_broadcaster/actions/workflows/ros2-build.yml/badge.svg)](https://github.com/RbSCR/imu_sensor_covariance_broadcaster/actions/workflows/ros2-build.yml)

- [imu\_sensor\_covariance\_broadcaster](#imu_sensor_covariance_broadcaster)
  - [Overview](#overview)
  - [Features](#features)
    - [Parameters](#parameters)
    - [State interfaces](#state-interfaces)
    - [PluginLib library](#pluginlib-library)
  - [Status](#status)

## Overview

Broadcaster to publish readings of an IMU with dynamic covariance from the IMU.

Can be used with IMUs like the BNO08x.

## Features

- Determines the covariance's (matrix diagonal) for each sensor in the broadcasted imu message based upon the sensors (singular) covariance value in the state interfaces.

### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `sensor_name` | string | Defines sensor name used as prefix for its interfaces |
| `frame_id` | string | Sensor's frame_id in which values are published |
| `rotation_offset: roll` | double | Roll offset value in radians. (Z-Y'-X'' convention) |
| `rotation_offset: pitch` | double | Pitch offset value in radians. (Z-Y'-X'' convention) |
| `rotation_offset: yaw` | double | Yaw offset value in radians. (Z-Y'-X'' convention) |

### State interfaces

| Interface | Unit | Notes |
| --------- | ---- | ----- |
| `orientation.x` | – | Quaternion X |
| `orientation.y` | – | Quaternion Y |
| `orientation.z` | – | Quaternion Z |
| `orientation.w` | – | Quaternion W |
| `angular_velocity.x` | rad/s | Gyroscope X |
| `angular_velocity.y` | rad/s | Gyroscope Y |
| `angular_velocity.z` | rad/s | Gyroscope Z |
| `linear_acceleration.x` | m/s² | Accelerometer X |
| `linear_acceleration.y` | m/s² | Accelerometer Y |
| `linear_acceleration.z` | m/s² | Accelerometer Z |
| `orientation_covariance` | – | Orientation covariance |
| `angular_velocity_covariance` | - | Gyroscope covariance |
| `linear_acceleration_covariance` | - | Accelerometer covariance |

### PluginLib library

Controller/broadcaster to publish readings of IMU sensors with dynamic covariance from the sensor.
Pluginlib-Library: imu_sensor_covariance_broadcaster
Plugin: imu_sensor_covariance_broadcaster/IMUSensorCovarianceBroadcaster (controller_interface::ControllerInterface)

## Status

- Tested and validated on Raspberry Pi 5 running ROS 2 Kilted/2026-08-21 (Ubuntu 24.04, aarch64) using BNO085 hardware.
- Work in progress
