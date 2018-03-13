The purpose of this folder is to self-contain the files needed to demostrate the basics of YANG models and tools.

See the tree of a module using pyang -f tree. For instance:
`pyang -f tree bgp_example.yang`

To validate the XML, run
```
sudo apt-get install xsltproc
sudo apt-get install libxml2-utils
export YANG_MODPATH=$YANG_MODPATH:~/local_notebook/SDNMeetupYDK/Models/
yang2dsdl -v  bgp_example.xml -t config bgp_example.yang
```
