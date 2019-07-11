# Visualizing Models and Python Classes

## Yang Model Tree for Implemented Models on Rosetta
**a trimmed down pyang snippet for just the yang models that currently have parsers/translators for the project**
```
+--rw openconfig-interfaces:interfaces
|  +--rw interface* [name]
|     +--rw openconfig-if-aggregate:aggregation
|     |  +--rw config
|     |  |  +--rw lag-type? <aggregation-type(enumeration)>
|     |  |  +--rw min-links? <uint16>
|     |  +--rw openconfig-vlan:switched-vlan
|     |     +--rw config
|     |     |  +--rw access-vlan? <vlan-id(uint16)>
|     |     |  +--rw interface-mode? <vlan-mode-type(enumeration)>
|     |     |  +--rw native-vlan? <vlan-id(uint16)>
|     |     |  +--rw trunk-vlans* <union>
|     |     +--ro state
|     |        +--ro access-vlan? <vlan-id(uint16)>
|     |        +--ro interface-mode? <vlan-mode-type(enumeration)>
|     |        +--ro native-vlan? <vlan-id(uint16)>
|     |        +--ro trunk-vlans* <union>
|     +--rw config
|     |  +--rw description? <string>
|     |  +--rw enabled? <boolean>
|     |  +--rw loopback-mode? <boolean>
|     |  +--rw mtu? <uint16>
|     |  +--rw name? <string>
|     |  +--rw openconfig-vlan:tpid? <identityref>
|     |  +--rw type <identityref>
|     +--rw openconfig-if-ethernet:ethernet
|     |  +--rw config
|     |  |  +--rw openconfig-if-aggregate:aggregate-id? <leafref>
|     |  |  +--rw auto-negotiate? <boolean>
|     |  |  +--rw duplex-mode? <enumeration>
|     |  |  +--rw enable-flow-control? <boolean>
|     |  |  +--rw mac-address? <mac-address(string)>
|     |  |  +--rw port-speed? <identityref>
|     |  |  +--ro enable-flow-control? <boolean>
|     |  |  +--ro hw-mac-address? <mac-address(string)>
|     |  |  +--ro mac-address? <mac-address(string)>
|     |  |  +--ro negotiated-duplex-mode? <enumeration>
|     |  |  +--ro negotiated-port-speed? <identityref>
|     |  |  +--ro port-speed? <identityref>
|     |  +--rw openconfig-vlan:switched-vlan
|     |     +--rw config
|     |     |  +--rw access-vlan? <vlan-id(uint16)>
|     |     |  +--rw interface-mode? <vlan-mode-type(enumeration)>
|     |     |  +--rw native-vlan? <vlan-id(uint16)>
|     |     |  +--rw trunk-vlans* <union>
|     |     +--ro state
|     |        +--ro access-vlan? <vlan-id(uint16)>
|     |        +--ro interface-mode? <vlan-mode-type(enumeration)>
|     |        +--ro native-vlan? <vlan-id(uint16)>
|     |        +--ro trunk-vlans* <union>
|     +--rw name <leafref>
|     +--rw openconfig-vlan:routed-vlan
|     |  +--rw config
|     |  |  +--rw vlan? <union>
|     |  +--rw openconfig-if-ip:ipv4
|     |  |  +--rw addresses
|     |  |  |  +--rw address* [ip]
|     |  |  |     +--rw config
|     |  |  |     |  +--rw ip? <ipv4-address(string)>
|     |  |  |     |  +--rw prefix-length? <uint8>
|     |  |  |     +--rw ip <leafref>
|     |  |  |     +--ro state
|     |  |  +--rw config
|     |  |  |  +--rw dhcp-client? <boolean>
|     |  |  |  +--rw enabled? <boolean>
|     |  |  |  +--rw mtu? <uint16>
|     +--rw subinterfaces
|        +--rw subinterface* [index]
|           +--rw config
|           |  +--rw description? <string>
|           |  +--rw enabled? <boolean>
|           |  +--rw index? <uint32>
|           +--rw index <leafref>
|           +--rw openconfig-vlan:vlan
|              +--rw config
|              |  +--rw vlan-id? <union>
|              +--rw egress-mapping
|              |  +--rw config
|              |  |  +--rw tpid? <identityref>
|              |  |  +--rw vlan-id? <vlan-id(uint16)>
|              |  |  +--rw vlan-stack-action? <vlan-stack-action(enumeration)>
+--rw openconfig-network-instance:network-instances
|  +--rw network-instance* [name]
|     +--rw afts
|     |  +--rw ethernet
|     |  |  +--rw mac-entry* [mac-address]
|     |  |     +--rw config
|     |  |     |  +--rw mac-address? <mac-address(string)>
|     |  |     +--rw mac-address <leafref>
|     +--rw config
|     |  +--rw description? <string>
|     |  +--rw enabled? <boolean>
|     |  +--rw enabled-address-families* <identityref>
|     |  +--rw mtu? <uint16>
|     |  +--rw name? <string>
|     |  +--rw route-distinguisher? <route-distinguisher(union)>
|     |  +--rw router-id? <dotted-quad(string)>
|     |  +--rw type? <identityref>
|     +--rw interfaces
|     |  +--rw interface* [id]
|     |     +--rw config
|     |     |  +--rw associated-address-families* <identityref>
|     |     |  +--rw id? <string>
|     |     |  +--rw interface? <leafref>
|     |     |  +--rw subinterface? <leafref>
|     |     +--rw id <leafref>
|     |     +--ro state
|     |        +--ro associated-address-families* <identityref>
|     |        +--ro id? <string>
|     |        +--ro interface? <leafref>
|     |        +--ro subinterface? <leafref>
```

## Python Class UML diagram for Yangify and Rosetta Python Classes

I used this tool:
https://www.pynsource.com/download.html
to take the Yangify Python classes and the NTC-Rosetta Python classes into UML diagrams. 

Hopefully this shows the relationships between all the moving parts, especially since the rosetta translation and parsing activites are using python class inheritance. 

I have put the *.pyns files in this repo I used to create the UML diagrams, but you can view the screen shots for simplicity. 

### Yangify UML
Inline-style: 
![alt text](https://github.com/jabelk/yangify_rosetta_model_visuals/blob/master/Yangify_uml.png "Logo Title Text 1")

### yangify and rosetta translate UML
Inline-style: 
![alt text](https://github.com/jabelk/yangify_rosetta_model_visuals/blob/master/yangify_rosetta_translate.png "Logo Title Text 1")


### yangify and rosetta parser for vlan only UML
Inline-style: 
![alt text](https://github.com/jabelk/yangify_rosetta_model_visuals/blob/master/yangify_rosetta_parser_vlan.png "Logo Title Text 1")

### yangify and rosetta parser for interfaces only UML
Inline-style: 
![alt text](https://github.com/jabelk/yangify_rosetta_model_visuals/blob/master/yangify_rosetta_parser_interfaces.png "Logo Title Text 1")