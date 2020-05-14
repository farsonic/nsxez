## NSXEZ

NSXEZ is a Python library to remotely manage/automate NSX-T platforms. The user is NOT required to be a Software Programmer, or have sophisticated knowledge of NSX-T environments, or have a complex understanding of the NSX-T REST API. It does however expect that someone has built a functional NSX-T environment which includes a functional Tier-0 router and potentially edge gatway services...if you expect to have any decent functionality. 


## Installation

Installation requires Python 2.7 or 3.X and the associated python pip tool. The only other requirements currently as the requests and uuid libraries which are installed automatically through pip. To install NSXEZ simply use the following command from your shell, provided pip is installed and operational. 

`
pip install nsxez
`

## Upgrade

Upgrading has the same requirements as installation and has the same format for install with the addition of -U 

`
pip install -U nsxez
`

## Inital usage

Teh library operates on a preexisting Tier0 router and when initiated it expects you to pass a valid NSX-T manager IP address, username, password and Tier0 router name. All ongoing operations are performed against this Tier0 router enviornment. 

```python
from nsxez import operations
nsx = operations.device("192.168.0.22","admin","VMware1!VMware1!","Peering")
```

Example creating a new VRF called "Blue". Values to be passed are the name of the VRF, the Route Target (used for import and export) as well as the unique route distinguisher and the VNI for VXLAN overlay from the edge node to the peer. 

```python
from nsxez import operations as nsx
dev = nsx.device("192.168.0.22","admin","VMware1!VMware1!","Peering")
dev.set_routing_instance("VRF_1238","65000:7001","7001","79423")
```

Example output gathering route table for VRF "Blue"

```python
from nsxez import operations as nsx
dev = nsx.device("192.168.0.22","admin","VMware1!VMware1!","Peering")
dev.get_routing_instance("Blue")
```
