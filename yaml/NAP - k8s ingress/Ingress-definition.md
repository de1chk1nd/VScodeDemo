https://docs.nginx.com/nginx-ingress-controller/app-protect/configuration/
--------------------------------------------------------------------------

You can define App Protect policies for your Ingress resources by creating an APPolicy Custom Resource.

To add any App Protect policy to an Ingress resource:

Create an APPolicy Custom resource manifest.

Add the desired policy to the spec field in the APPolicy resource.

Note: The relationship between the Policy JSON and the resource spec is 1:1. If you’re defining your resources in YAML, as we do in our examples, you’ll need to represent the policy as YAML. The fields must match those in the source JSON exactly in name and level.

--------------------------------------------------------------------------

{
    "policy": {
        "name": "dataguard_blocking",
        "template": {
            "name": "POLICY_TEMPLATE_NGINX_BASE"
        },
        "applicationLanguage": "utf-8",
        "enforcementMode": "blocking",
        "blocking-settings": {
            "violations": [
                {
                    "name": "VIOL_DATA_GUARD",
                    "alarm": true,
                    "block": true
                }
            ]
        },
        "data-guard": {
            "enabled": true,
            "maskData": true,
            "creditCardNumbers": true,
            "usSocialSecurityNumbers": true,
            "enforcementMode": "ignore-urls-in-list",
            "enforcementUrls": []
        }
    }
}


# # # # # # # # # #
# # # # # # # # # #

apiVersion: appprotect.f5.com/v1beta1
kind: APPolicy
metadata: 
  name: dataguard-blocking
spec:
  policy:
    name: dataguard_blocking
    template: 
      name: POLICY_TEMPLATE_NGINX_BASE
    applicationLanguage: utf-8
    enforcementMode: blocking 
    blocking-settings:
      violations:
      - name: VIOL_DATA_GUARD
        alarm: true
        block: true
    data-guard:
      enabled: true
      maskData: true
      creditCardNumbers: true
      usSocialSecurityNumbers: true
      enforcementMode: ignore-urls-in-list
      enforcementUrls: []