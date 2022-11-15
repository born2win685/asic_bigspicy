# Spice Simulation and STA using BIGSPICY

bigspicy is a tool for merging circuit descriptions (netlists), generating Spice decks modeling those circuits, generating Spice tests to measure those models, and analyzing the results of running Spice on those tests.My part of the project is to create the circuit protobuf.
# Tools Required

- ``` Icarius Verilog ```
- ``` Python3 ```
- ``` Xdm ``` tool for converting the spice files to ``` xyce ``` format.
- ``` bigspicy ``` for making a single circuit protobuf
- ``` xyce ``` for performing test

# Installation of tools

## Icarius verilog

``` 
sudo apt-get install iverilog
```
# Pre-requesites
## Converting SPICE files 

The spice files should be in xyce format.The convertion was done in the following repository.

https://github.com/LokeshMaji

## Compiling Protobufs

We have to compile the protobufs into the python file.
```
git submodule update --init   
protoc --proto_path vlsir vlsir/*.proto vlsir/*/*.proto --python_out=.
protoc proto/*.proto --python_out=.

```
# Merging files into Circuit protobuf

The files are now merged into circuit protobuf.This (final.pb) can be used to generate whole module spice models.
We can use that to conduct various tests using xyce.Type the following (after cloning this directory) to merge the files.

```
./bigspicy.py \
    --import \
    --verilog src/iiitb_counter.synth.v \
    --spef src/iiitb_counter.spef \
    --spice_header lib/sky130_fd_sc_hd.spice \
    --top iiitb_counter \
    --save final.pb \
    --working_dir /tmp/bigspicy

```
# Contributors 

- **B Sathiya Naraayanan** 
- **Kunal Ghosh** 



# Acknowledgments


- Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.

# Contact Information

- B Sathiya Naraayanan, IMT2020534, International Institute of Information Technology, Bangalore  ,Sathiya.Naraayanan@iiitb.ac.in
- Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. kunalghosh@gmail.com

# References

- [Bigspicy github](https://github.com/google/bigspicy)




