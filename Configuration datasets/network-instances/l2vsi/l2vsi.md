# L2VSI (L2 virtual switch instance)

## URL

```
frinx-openconfig-network-instance:network-instances/network-instance/{{vsi_ni_name}}
```

## OPENCONFIG YANG

```javascript
{
    "network-instance": [
        {
            "config": {
                "name": "{{vsi_ni_name}}"
                "description": "{{vsi_ni_description}}"
                "type": "L2VSI"
                "enabled": true
                "frinx-saos-vs-extension:encap-cos-policy": {{vsi_ni_encap_cos_policy}}
                "frinx-saos-vs-extension:encap-fixed-dot1dpri": {{vsi_ni_encap_fixed_dot1dpri}}
            }
            "connection-points": {
                "connection-point": [
                    {
                        "connection-point-id": "{{vsi_cp_name}}",
                        "config": {
                            "connection-point-id": "{{vsi_cp_name}}"
                        } 
                    }
                ]
            }
            "interfaces": {
                "interface": [
                    {
                        "id": "{{vsi_ni_if_name}}",
                        "config": {
                            "id": "{{vsi_ni_if_name}}"
                            "interface": "{{vsi_ni_if_name}}"
                        } 
                    }
                ]
            }

        }
    ]
}
```

## OS Configuration Commands

### Ciena SAOS 6.14

#### CLI

<pre>
virtual-switch ethernet create vs {{vsi_ni_name}} vc {{vsi_cp_name}}
virtual-switch ethernet set vs {{vsi_ni_name}} description {{vsi_ni_description}}
virtual-switch ethernet set vs {{vsi_ni_name}} encap-cos-policy {{vsi_ni_encap_cos_policy}}
virtual-switch ethernet set vs {{vsi_ni_name}} encap-fixed-dot1dpri {{vsi_ni_encap_fixed_dot1dpri}}
virtual-switch ethernet add vs {{vsi_ni_name}} port {{vsi_ni_if_name}}
port set port {{vsi_ni_if_name}} untagged-ctrl-vs {{vsi_ni_name}}
port set port {{vsi_ni_if_name}} untagged-data-vs {{vsi_ni_name}}
</pre>

{{vsi_ni_encap_cos_policy}} can have values <dot1dpri-inherit | fixed | ip-prec-inherit | phbg-inherit | port-inherit | vs-inherit>  


##### Unit

