#!/usr/bin/env python

from ansible.module_utils.basic import AnsibleModule
from ydk.providers import NetconfServiceProvider
from ydk.services import CRUDService
from ydk.models.cisco_ios_xr import Cisco_IOS_XR_ip_static_cfg as xr_ip_static_cfg

ANSIBLE_METADATA = { 'metadata_version': '1.0', 'supported_by': 'community', 'status': ['preview']}

DOCUMENTATION = """
---
module: ydk_xr_static_route 
short_description: Create static route in devices supporting module Cisco_IOS_XR_ip_static_cfg.
description:
        - Uses module Cisco_IOS_XR_ip_static_cfg to configure a static route.
        - Incomplete implementation, just for demostration purposes.
options:
        address_family_ip:
                description: 
                        - ipv4 only accepted now
                default: ipv4
        address_family_prefix_type:
                description: 
                        - unicast only accepted now 
                default: unicast
        prefix:
                description:
                        - Prefix to specify in the static route
                type: string
        prefix_length:
                description:
                        - Length of prefix in static route.
                type: int
        next_hop:
                description:
                        - Next-hop to use in the static route.
        vrf:
                description:
                        - Vrf where static route is installed. We currenlty only accept default 
                type: string
                required: false
                default: default
"""
EXAMPLES = """
- ydk_xr_static_route:
  - prefix: "1.1.1.1"
  - prefix_length: 32
  - next_hop: "2.2.2.2"
"""

RETURN = """
"""

def validate_address_family_ip(address_family_ip):
    if address_family_ip not in set(['ipv4']):
        return False
    return True

def validate_address_family_prefix_type(address_family_prefix_type):
    if address_family_prefix_type not in set(['unicast']):
        return False
    return True

def validate_vrf(vrf):
    if vrf == "default":
        return True
    return False

if __name__ == '__main__': 
    module = AnsibleModule(
            argument_spec=dict(
                address_family_ip=dict(type='str', required=False, default="ipv4"), 
                address_family_prefix_type=dict(type='str', required=False, default="unicast"), 
                prefix=dict(type='str', required=True), 
                prefix_length=dict(type='int', required=True), 
                next_hop=dict(type='str', required=True), 
                vrf=dict(type='str', required=False, default="default"),),
            supports_check_mode=True)

    if module.check_mode: 
        module.exit_json(changed=False)

    address_family_ip = module.params["address_family_ip"]
    address_family_prefix_type = module.params["address_family_prefix_type"]
    prefix = module.params["prefix"]
    prefix_length = module.params["prefix_length"]
    next_hop = module.params["next_hop"]
    vrf  = module.params["vrf"]

    if not validate_vrf(vrf):
        module.fail_json(msg='vrf {} is not valid.'.format(vrf))
    if not validate_address_family_ip(address_family_ip):
        module.fail_json(msg='address_family_ip {} is not valid.'.format(address_family_ip))
    if not validate_address_family_prefix_type(address_family_prefix_type):
        module.fail_json(msg='address_family_prefix_type {} is not valid.'.format(address_family_prefix_type))

    # We'll be hard-coding the connectivity on this example, but you you can add that to the input as an exercise.
    router = "192.168.10.4"
    port = 830
    username = "vagrant"
    password = "vagrant"
    protocol = "ssh"
    provider = NetconfServiceProvider(address=router,
            port=port,
            username=username,
            password=password, 
            protocol=protocol)
    crud = CRUDService()
    # YOUR CODE GOES HERE (JUST COPY FROM IT FROM THE NOTEBOOK) 







    try:
        #crud.create(provider, static_route_object)
    except Exception as e:
        module.fail_json(msg='static route transaction failed. Error is: {}'.format(e))

    module.exit_json(changed=True)
