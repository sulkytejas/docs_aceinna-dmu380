CAN J1939 Data Messages
***********************

.. contents:: Contents
    :local:

.. toctree::
    :maxdepth: 1


The following Data messages are implemented in the example applications.
The user can modify provided messages or add messages as needed.
The rate of data messages can be configured by SET commands.

.. table:: *Data Messages*
    :align: left

    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    | **Data Packet**   | **PF** | **PS** | **PGN**  | **Data Length**     |  **Purpose**                    |
    |                   | (dec)  | (dec)  |   (dec)  | (bytes)             |                                 |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    || Slope Sensor     | 240    | 41     | 61481    |  8                  || Provide high accuracy          |
    || Information      |        |        |          |                     || pitch & roll rates             |
    |  Type 2           |        |        |          |                     |                                 |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    || Angular Rate     | 240    | 42     | 61482    |  8                  || Provide moderate accuracy      |
    || Sensor Data      |        |        |          |                     || pitch, roll and yaw rates      |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    || Acceleration     | 240    | 45     | 61485    |  8                  || Provide moderate accuracy      |
    || Sensor Data      |        |        |          |                     || X, Y, and Z axes acceleration  |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    || Magnetometer     | 255    | 106    | 65386    |  8                  || Provide readings from magnetic |
    || Sensor Data      |        |        |          |                     || sensor for X, Y, and Z axes    |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+

|
|
|

.. table:: *Data message for INS application*
    :align: left

    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    | **Data Packet**   | **PF** | **PS** | **PGN**  | **Data Length**     |  **Purpose**                    |
    |                   | (dec)  | (dec)  |   (dec)  | (bytes)             |                                 |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    || GPS              | 248    | 02     | 129026   |  8                  || Provide high accuracy          |
    || Position Data    |        |        |          |                     || latitude & longitude rates     |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    || Rapid            | 248    | 01     | 129025   |  8                  || Provide high accuracy          |
    || Update Data      |        |        |          |                     || cog and sog                    |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
    || Attitude         | 241    | 25     | 127257   |  8                  || Provide high accuracy          |
    || Data             |        |        |          |                     || yaw, pitch and roll            |
    +-------------------+--------+--------+----------+---------------------+---------------------------------+
   

|
|
|
	
**Slope Sensor Information - Type 2 (SSI2) Data Packet**


The following table describes the SSI2 Data Packet Payload:

.. table:: *SSI2 Data Packet Payload*
    :align: left

    +------------+----------------+------------------+-----------------+------------+
    | **Bytes**  | **Field Name** | **Range**        | **Resolution**  | **Offset** |
    +------------+----------------+------------------+-----------------+------------+
    | 0:2        | Pitch          | -250 to +252 deg | 1/32768 deg/bit | -250 deg   |
    +------------+----------------+------------------+-----------------+------------+
    | 3:5        | Roll           | -250 to +252 deg | 1/32768 deg/bit | -250 deg   |
    +------------+----------------+------------------+-----------------+------------+
    | 6:7        | FoM,Latency    | Ignore           | Ignore          | Ignore     |
    +------------+----------------+------------------+-----------------+------------+

|
|
|
	
**Angular Rate Data Packet**


The following table describes the Angular Rate Data Packet:

.. table:: *Angular Rate Data Packet Payload*
    :align: left

    +----------------+----------------+--------------------+----------------------+------------+
    | **Byte Number**| **Parameter**  | **Range**          | **Resolution**       | **Offset** |
    +----------------+----------------+--------------------+----------------------+------------+
    | 0:1            | Angular Rate X | -250 to +252 deg/s | 1/128 deg/second/bit | -250 deg   |
    +----------------+----------------+--------------------+----------------------+------------+
    | 2:3            | Angular Rate Y | -250 to +252 deg/s | 1/128 deg/second/bit | -250 deg   |
    +----------------+----------------+--------------------+----------------------+------------+
    | 4:5            | Angular Rate Z | -250 to +252 deg/s | 1/128 deg/second/bit | -250 deg   |
    +----------------+----------------+--------------------+----------------------+------------+
    | FoM,Latency    | FoM,Latency    | Ignore             | Ignore               | Ignore     |
    +----------------+----------------+--------------------+----------------------+------------+

|
|	
|

**Acceleration Data Packet**

The following table describes the Acceleration Data Packet:

.. table:: *Acceleration Data Packet Payload*
    :align: left

    +------------+--------------------+-----------------------+-----------------+-------------+
    || **Byte**  |  **Parameter**     | **Range**             | **Resolution**  | **Offset**  |
    || **Number**|                    |                       |                 |             |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 0:1        | Acceleration X     | -320 to 320/55 m/s**2 | 0.01 m/s**2/bit | -320 m/s**2 |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 2:3        | Acceleration Y     | -320 to 320/55 m/s**2 | 0.01 m/s**2/bit | -320 m/s**2 |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 4:5        | Acceleration Z     | -320 to 320/55 m/s**2 | 0.01 m/s**2/bit | -320 m/s**2 |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 6:7        | FoM,Latency        | Ignore                | Ignore          | Ignore      |
    +------------+--------------------+-----------------------+-----------------+-------------+

|
|	
|	
	
**Magnetometer Data Packet**

The following table describes the Magnetometer Data Packet:

.. table:: *Magnetometer Data Packet Payload*
    :align: left

    +------------+--------------------+-----------------------+-----------------+-------------+
    || **Byte**  || **Parameter**     | **Range**             | **Resolution**  | **Offset**  |
    || **Number**||                   |                       |                 |             |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 0:1        | Magnetic Field X   | -8 to 8 Gauss         | 4000 LSB/G      | -8 Gauss    |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 2:3        | Magnetic Field Y   | -8 to 8 Gauss         | 4000 LSB/G      | -8 Gauss    |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 4:5        | Magnetic Field Z   | -8 to 8 Gauss         | 4000 LSB/G      | -8 Gauss    |
    +------------+--------------------+-----------------------+-----------------+-------------+
    | 6:7        | FoM,Latency        | Ignore                | Ignore          | Ignore      |
    +------------+--------------------+-----------------------+-----------------+-------------+

.. note::   As with all multiple byte fields, the LSB of each of the Data Packet fields is transmitted first.

**GPS Position Information - Data Packet**


The following table describes the Data Packet Payload:

.. table:: *Data Packet Payload*
    :align: left

    +------------+----------------+------------------+--------------------+------------+
    | **Bytes**  | **Field Name** | **Range**        | **Resolution**     | **Offset** |
    +------------+----------------+------------------+--------------------+------------+
    | 0:3        | Latitude       | -210 to +210 deg | 1/10000000 deg/bit | 210 deg    |
    +------------+----------------+------------------+--------------------+------------+
    | 4:7        | Longitude      | -210 to +210 deg |  1/10000000 deg/bit| 210 deg    |
    +------------+----------------+------------------+--------------------+------------+

|
|
|

**Rapid Update - Data Packet**


The following table describes the Data Packet Payload:

.. table:: *Data Packet Payload*
    :align: left

    +------------+----------------+------------------+--------------------+------------+
    | **Bytes**  | **Field Name** | **Range**        | **Resolution**     | **Offset** |
    +------------+----------------+------------------+--------------------+------------+
    | 2:3        | COG            | -250 to +252 rad | 1/10000 rad/bit    | 0          |
    +------------+----------------+------------------+--------------------+------------+
    | 4:5        | SOG            | -250 to +252 ms  |  1/100 ms/bit|.    | 0          |
    +------------+----------------+------------------+--------------------+------------+

|
|
|

**Attitude - Data Packet**


The following table describes the Data Packet Payload:

.. table:: *Data Packet Payload*
    :align: left

    +------------+----------------+-------------------+-----------------+------------+
    | **Bytes**  | **Field Name** | **Range**         | **Resolution**  | **Offset** |
    +------------+----------------+-------------------+-----------------+------------+
    | 1:2        | YAW            | -3.14 to +3.14 rad| 1/10000 rad/bit | 3.145      |
    +------------+----------------+-------------------+-----------------+------------+
    | 4:5        | PITCH          | -3.14 to +3.14 ms | 1/100 ms/bit    | 3.145      |
    +------------+----------------+-------------------+-----------------+------------+
    | 4:5        | ROLL           | -3.14 to +3.14 ms | 1/100 ms/bit    | 3.145      |
    +------------+----------------+-------------------+-----------------+------------+

|
|
|
