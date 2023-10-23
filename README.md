# DCI_decoder_LTE

DCI message decoding
The Trace_DATE.csv file contains, among other information, the payload of the DCI messages. The payload is a string of bits that must be decoded according to 3GPP specifications. For this purpose, we
execute the DCIdecoder.py to decode the trace file created by the LTEanalyzer.

A new csv file Trace_DATE_with_id.csv is created which contains the information carried by the control messages. This file will be used for the machine learning model.

In the Trace_DATE_with_id.csv file, each row represents a DCI message, and the columns include the following features:
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
considered as connections established by the terminals. DCI format 0 is used for uplink and DCI format 1A and 2 for downlink.
