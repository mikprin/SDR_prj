# Simple FM transmitter using gnuradio
Cool source for this: https://wiki.opendigitalradio.org/Simple_FM_transmitter_using_gnuradio

<!-- Simple FM transmitter using gnuradio. -->

Tools needed:

* gnuradio 3.2
* grc (gnuradio companion)
* mpg123
* USRP 

Mono FM transmission is very simple as all necessary blocks already exist in gnuradio. In this example we will show how to make a FM transmission from an mp3 stream for an Internet radio. Look at GRC schema or use directly python code below.

Input file is a unix FIFO file that means that we need to feed it externally from the shell using these commands:

Creation of the FIFO file (once):

`mkfifo stream_32k.fifo`

Decoding of an mp3 Internet radio station stream, conversion and output of raw linear samples to the FIFO:

`mpg123 -r32000 -m -s  http://maxxima.mine.nu:8000 >stream_32k.fifo`

Option "-m" is to convert stream to mono, "-r32000" perform sample rate conversion to 32kHz. 