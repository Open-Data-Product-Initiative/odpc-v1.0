# ProductReference

The `ProductReference` object connects an ODPC catalog to the actual source definition of a data product. It does not redefine the full data product. It provides a stable catalog-level reference to a product described in ODPS, DPDS, an internal enterprise template, a vendor catalog, a marketplace definition, or another metadata source.

`ProductReference` is the bridge between the portfolio layer and the product definition layer. It allows catalogs, use cases, objectives, KPIs, and signals to point to data products without copying the full product metadata into ODPC.

A `ProductReference` should include enough information for discovery, ownership, lifecycle visibility, and system integration. The complete product details remain in the source model referenced by `uri`, `identifier`, or another system-specific reference.

By separating the catalog reference from the source product definition, ODPC supports mixed data product environments where products may be described using different standards, platforms, and internal models.

## Mandatory attributes and options

> Example of productReference object usage:

```yml
productReference:
  id: DP-001
  productID: urbanpulse-events
  productVersion: "1.0.0"
  name:
    en: UrbanPulse Events Data Product
  description:
    en: Data product providing event information for urban analytics and citizen services.
  productModel:
    standard: ODPS
    version: "4.1"
    format: yaml
    uri: https://example.org/products/urbanpulse-events/odps.yaml
```

| Attribute               | Type   | Options                           | Description                                                                                      |
| ----------------------- | ------ | --------------------------------- | ------------------------------------------------------------------------------------------------ |
| `productReference`      | object | required                          | Top-level object that defines a lightweight catalog reference to a data product.                 |
| `id`                    | string | required                          | Stable identifier for the product reference inside ODPC.                                         |
| `productID`             | string | required                          | Product identifier aligned with the referenced data product.                                     |
| `productVersion`        | string | required                          | Version of the data product shown in the catalog.                                                |
| `name`                  | object | required, language-tagged strings | Human-readable product name.                                                                     |
| `name.en`               | string | required                          | English product name.                                                                            |
| `description`           | object | required, language-tagged strings | Short product description used for catalog display and discovery.                                |
| `description.en`        | string | required                          | English product description.                                                                     |
| `productModel`          | object | required                          | Defines the authoritative product model or specification the catalog reference points to.        |
| `productModel.standard` | string | required                          | Product model or standard used by the referenced product, such as `ODPS`, `DPDS`, or `internal`. |
| `productModel.version`  | string | required                          | Version of the referenced product model or standard, such as ODPS `4.1`.                         |
| `productModel.format`   | string | required                          | Format of the referenced product model, such as `yaml`, `json`, or `html`.                       |
| `productModel.uri`      | string | required                          | URI pointing to the authoritative product definition.                                            |



## Optional attributes and options

> Example of productReference object usage:

```yml
productReference:
  id: DP-001
  productID: urbanpulse-events
  productVersion: "1.0.0"

  name:
    en: UrbanPulse Events Data Product

  description:
    en: Data product providing event information for urban analytics and citizen services.

  valueProposition:
    en: Supports event-based mobility planning, citizen services, and urban operations.

  visibility: public
  status: production
  type: dataset

  domains:
    - smart-city
    - mobility

  categories:
    - urban analytics
    - citizen services

  standards:
    - ODPS

  tags:
    - events
    - smart-city
    - mobility

  portfolioPriority: high
  governanceProfile: structured

  owner:
    organization: Example Organization
    team: Urban Analytics
    role: Data Product Owner

  productModel:
    standard: ODPS
    version: "4.1"
    format: yaml
    uri: https://example.org/products/urbanpulse-events/odps.yaml

  logoURL: https://example.org/assets/urbanpulse-logo.png

  outputFileFormats:
    - JSON
    - CSV
```

| Attribute             | Type             | Options                           | Description                                                                                                                                                                                                                                                                         |
| --------------------- | ---------------- | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `valueProposition`    | object           | optional, language-tagged strings | Short explanation of the value the product provides.                                                                                                                                                                                                                                |
| `valueProposition.en` | string           | optional                          | English value proposition.                                                                                                                                                                                                                                                          |
| `visibility`          | string           | optional                          | Product visibility, such as `public`, `internal`, `restricted`, or `private`.                                                                                                                                                                                                       |
| `status`              | string           | optional                          | Lifecycle status of the product, such as `draft`, `active`, `production`, `deprecated`, or `retired`.                                                                                                                                                                               |
| `type`                | string           | optional                          | Type of data product. One of: `raw data`, `derived data`, `dataset`, `reports`, `analytic view`, `3D visualisation`, `algorithm`, `decision support`, `automated decision-making`, `data-enhanced product`, `data-driven service`, `data-enabled performance`, or `bi-directional`. |
| `domains`             | array of strings | optional                          | Business, operational, policy, or industry domains related to the product.                                                                                                                                                                                                          |
| `categories`          | array of strings | optional                          | Catalog categories used for grouping and browsing.                                                                                                                                                                                                                                  |
| `standards`           | array of strings | optional                          | Standards or specifications associated with the product, such as `ODPS`, `DCAT`, or `OpenAPI`.                                                                                                                                                                                      |
| `tags`                | array of strings | optional                          | Keywords used to classify, search, or filter the product reference.                                                                                                                                                                                                                 |
| `portfolioPriority`   | string           | optional                          | Relative portfolio importance, such as `low`, `medium`, `high`, or `critical`.                                                                                                                                                                                                      |
| `governanceProfile`   | string           | optional                          | Governance posture or profile used to classify the product in the catalog.                                                                                                                                                                                                          |
| `owner`               | object           | optional                          | Ownership information for the product.                                                                                                                                                                                                                                              |
| `owner.organization`  | string           | optional                          | Organization responsible for the product.                                                                                                                                                                                                                                           |
| `owner.team`          | string           | optional                          | Team responsible for the product.                                                                                                                                                                                                                                                   |
| `owner.role`          | string           | optional                          | Responsible role, such as Data Product Owner or Product Manager.                                                                                                                                                                                                                    |
| `logoURL`             | string           | optional                          | URL to a logo or visual asset used in catalog display.                                                                                                                                                                                                                              |
| `outputFileFormats`   | array of strings | optional                          | Output formats available from the product, such as `CSV`, `JSON`, `Parquet`, or `GeoJSON`.                                                                                                                                                                                          |


