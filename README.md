#include <wire.h>

#define mpu6050_address 0x01

#define power 0x6B
#define conf 0x1A // configration
#define gyro_conf 0x1B
#define accel_conf 0x2A
#define gyro_xout 0x2B
#define accel_xout 0x3A
#define gyro_xout 0x3B

void setup (){
    wire.begin();
    serial.begin(96000);

    wire.begintransmission(mpu6050_address);
    wire.write(gyro_conf);
    wire.write(accel_conf);
    wire.write(0);
    wire.endtransmission();//mpu6050 initialized
}

void loop (){

    int ax , ay , az ;
    int gx , gy , gz ;

    wire.begintransmission(mpu6050_address);
    wire.write(gyro_conf);
    wire.endtransmission();
    serial.println("data transmitted:  ");
    delay(1000);

    ax = wire.read();
    ay = wire.read();
    az = wire.read();

    wire.begintransmission(mpu6050_address);
    wire.write(accel_conf);
    wire.endtransmission();
    serial.println("data transmitted:  ");
    delay(1000);
    gx = wire.read();
    gy = wire.read();
    gz = wire.read();

    float gyro_yaw = gz 
    wire.println(gyro_yaw)
}  
