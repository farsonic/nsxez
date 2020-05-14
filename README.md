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

Example output gathering route table for VRF "Blue" 

```python
from nsxez import operations
nsx = operations.device("192.168.0.22","admin","VMware1!VMware1!","Peering")
nsx.get_route_table("Blue")
[{u'count': 17, u'route_entries': [{u'network': u'222.0.0.1/32', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'172.16.10.0/24', u'route_type': u't0c', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'10.10.0.0/24', u'route_type': u't0c', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'0.0.0.0/0', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'0.0.0.0/0', u'route_type': u'', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'127.0.0.3', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'10.22.12.0/24', u'route_type': u't0c', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'169.254.0.0/24', u'route_type': u't0c', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'222.0.0.0/24', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'10.10.0.254/32', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'ff02::2/128', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'::ffff:200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'fc7e:f206:db42::/48', u'route_type': u't0c', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'fc00::1/128', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'::ffff:200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'::/0', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'::ffff:200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'::/0', u'route_type': u'', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'::ffff:127.0.0.3', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'fe80::/64', u'route_type': u't0c', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'fc00::/64', u'route_type': u'b', u'admin_distance': 200, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'::ffff:200.0.0.1', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}, {u'network': u'ff00::/8', u'route_type': u'', u'admin_distance': 0, u'lr_component_id': u'4d16f3ef-ba97-4304-ad88-e525f0391c4f', u'next_hop': u'', u'lr_component_type': u'VRF_SERVICE_ROUTER_TIER0'}], u'edge_node': u'/infra/sites/default/enforcement-points/default/edge-clusters/bc85d6fc-4c52-45b3-8279-c19fe81795d2/edge-nodes/1936512d-e68b-48f3-bafc-5ef42a35eda8'}]
```


