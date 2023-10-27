# DCI_decoder_LTE

The TraceName.csv file created by the LTEanalyzer contains, among other information, the payload of the DCI messages. The payload is a string of bits that must be decoded according to 3GPP specifications. 

## Prerequisites
Before running the code, make sure you have the following libraries installed:
- [numpy](https://numpy.org/)
- [pandas](https://pandas.pydata.org/)

## Usage instructions
To decode the DCI payload of "TraceName.csv" which corresponds to monitoring the EARFCN band, run the following command:

```python3 DCIdecoder.py -t TraceName.csv -e EARFCN```

A new csv file TraceName_with_id.csv is created which contains the information carried by the control messages. In the TraceName_with_id.csv file, each row represents a DCI message, and the columns include the following features:
- Time: Unix timestamp in milliseconds 
- rnti: Radio Network Temporary Identifier (RNTI) associated with the DCI
- SFN: system frame number
- format: DCI format (0: format0, 2: format1A, 6: format2)
- preamble: random access preamble
- ta: first timing advance
- nb_TB: number of enabled transport blocks (TB)
- MCSi_1: Modulation Coding Scheme (MCS) index of the first transport block (-2: TB is disabled )
- MCSi_2: MCS index of the second transport block (-2: TB is disabled )
- TBS_1: TBS of first transport block (-2: TB is disabled )
- TBS_2: TBS of second transport block (-2: TB is disabled )
- nb_PRB: number of allocated PRBs
- connection_id: unique connection identifier

The RNTIs values 5, 65534, and 65535 are reserved for random access, paging messages, and system information. These values correspond to connection_id = {1, 2, 3}. These values should not be
considered as connections established by the terminals. DCI format 0 is used for uplink.
