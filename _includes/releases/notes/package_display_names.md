{% assign allPackagesSortedByDisplayName = allPackages | sort: 'DisplayName' %}
{% assign gaPackages = allPackagesSortedByDisplayName | where: "VersionType" , "GA" | map: 'DisplayName' | uniq %}
{% if gaPackages.size > 0 %}
#### Stable Packages ({{ gaPackages.size }})
{% for package in gaPackages %}
- {{ package }}
{% endfor %}
{% endif %}

{% assign patchPackages = allPackagesSortedByDisplayName | where: "VersionType", "Patch" | map: 'DisplayName' | uniq %}
{% if patchPackages.size > 0 %}
#### Patch Updates ({{ patchPackages.size }})
{% for package in patchPackages %}
- {{ package }}
{% endfor %}
{% endif %}

{% assign betaPackages = allPackagesSortedByDisplayName | where: "VersionType", "Beta" | map: 'DisplayName' | uniq %}
{% if betaPackages.size > 0 %}
#### Beta Packages ({{ betaPackages.size }})
{% for package in betaPackages %}
- {{ package }}
{% endfor %}
{% endif %}
