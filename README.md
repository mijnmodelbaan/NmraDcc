# NmraDcc
NMRA Digital Command Control (DCC) Library

This library allows you to interface to a NMRA DCC track signal and receive DCC commands.

The library currently supports the AVR ATTiny84/85 & ATMega88/168/328/32u4 and Teensy 3.x using the INT0/1 Hardware Interrupt and micros() ONLY and no longer uses Timer0 Compare Match B, which makes it much more portable to other platforms.

**Warning** as of version 1.4.4 support has been removed for the following two call-back functions, which will cause your sketch to silently stop working:

	extern void notifyDccAccState( uint16_t Addr, uint16_t BoardAddr, uint8_t OutputAddr, uint8_t State )
	extern void notifyDccSigState( uint16_t Addr, uint8_t OutputIndex, uint8_t State) 

To be able to use all the Pin Change Interrupts on the ATMega328, put the following lines on top of your sketch:

///////////////////////////////////////*********************************************************

// Uncomment to use the PinChangeInterrupts iso External Interrupts
#define PIN_CHANGE_INT

///////////////////////////////////////*********************************************************

Put these lines in your sketch BEFORE you #include the NmraDcc.h file.

Do NOT forget to set PIN to the correct value in your setup() routine.
