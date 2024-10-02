---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Empresa

En este sección se encuentran todos los endpoints para crear y gestionar empresas. Podrás crear empresas con el Bearer Token generado a través del Login mientras que el resto de las peticiones tendrás que usar la API Key de la empresa que deseas gestionar.



{% swagger src="../.gitbook/assets/GETCertifAPIKs.yaml" path="/api/list-api-keys/apikeys/{{id_company}}/list" method="get" %}
[GETCertifAPIKs.yaml](../.gitbook/assets/GETCertifAPIKs.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/GETCertifAPIKs.yaml" path="/api/certificates/{{id_company}}/list" method="get" %}
[GETCertifAPIKs.yaml](../.gitbook/assets/GETCertifAPIKs.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/Companies.yaml" path="/api/companies/{id_compary}/logo" method="post" %}
[Companies.yaml](../.gitbook/assets/Companies.yaml)
{% endswagger %}



:flag\_cl: :flag\_uy:

{% swagger src="../.gitbook/assets/Companies.yaml" path="/api/companies/{{id_company}}/enumeration/{{id_enumeration}}/config" method="put" %}
[Companies.yaml](../.gitbook/assets/Companies.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/CompaniesV2.yaml" path="/api/companies/{{id_company}}/enumeration/{{id_enumeration}}" method="delete" %}
[CompaniesV2.yaml](../.gitbook/assets/CompaniesV2.yaml)
{% endswagger %}

:flag\_cl: :flag\_uy:

{% swagger src="../.gitbook/assets/Companies.yaml" path="/api/companies/{{id_company}}/enumeration/list" method="get" %}
[Companies.yaml](../.gitbook/assets/Companies.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/CompaniesV2.yaml" path="/api/companies/apikey" method="post" %}
[CompaniesV2.yaml](../.gitbook/assets/CompaniesV2.yaml)
{% endswagger %}



{% swagger src="../.gitbook/assets/Companies.yaml" path="/api/companies" method="post" %}
[Companies.yaml](../.gitbook/assets/Companies.yaml)
{% endswagger %}



{% swagger src="../.gitbook/assets/Companies.yaml" path="/api/companies/{{id_company}}" method="put" %}
[Companies.yaml](../.gitbook/assets/Companies.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/CompaniesV2.yaml" path="/api/companies/{id_company}/certificates" method="post" %}
[CompaniesV2.yaml](../.gitbook/assets/CompaniesV2.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/CompaniesV2.yaml" path="/api/companies/{id_company}/enumeration/upload" method="post" %}
[CompaniesV2.yaml](../.gitbook/assets/CompaniesV2.yaml)
{% endswagger %}
