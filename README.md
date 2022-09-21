# Oscillera

<p align="left">
  <a href="https://www.oscillera.com/">
    <img src="oscilleraLogo.png" width="128" alt="Oscillera Logo">
  </a>
</p>

TEMPORARILY NOT RUNNING: I am currently working on a new version of Oscillera, the website is therefore temporarily shut down. The plan is for it to be up again and running somewhere in November 2022.

The project's name has changed to Oscillera from Ozzillate.

Oscillera is a web based application that allows you to send and receive files to and from nearby devices through the help of sound waves. You only need a speaker and a microphone, which means that the software can run on most older as well as newer hardware.

It works by temporarily uploading the file to the server (which is removed automatically within two minutes unless the transmitting client's browser tab is kept open for longer). The file gets assigned a randomly generated 64 bit ID, which is returned to the client to be broadcasted through sound. Finally, the receiver picks the ID up and downloads the file from the server.

The project's website can be found at: https://www.oscillera.com

## Sound Data Transfer

The data over sound communication works by uniquely mapping a combination of bits (in this case in a byte) to a combination of played tones given a set to choose from. The receiver runs a fourier transform on the raw microphone output to break the sound back into its respective tones (as well as filter out background noise) and maps them back to their corresponding bits. A CRC sum makes sure that the receiver does not request a non-existent file ID caused by random interference. The software is written in C++ and compiled to WebAssembly to faster run the rather computationally heavy fourier transforms.

Speed of the file ID transfer is currently at 10 bytes per second (including the 16-bit CRC), or approximately one 64-bit ID per second given that the data was not corrupted.

## Open Source?

If the project becomes open source in the future, all source code files together with build instructions will be uploaded to this repository.
