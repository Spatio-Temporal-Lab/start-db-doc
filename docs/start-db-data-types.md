# Data Types Supported by START-DB

## Numeric Data Type

| Data Type   | Name                             | Explanation                                                                 |
|:------------|:---------------------------------|:----------------------------------------------------------------------------|
| Integer/Int | Integer                          | The internal unified representation is Integer, and Int is the abbreviation |
| Long        | long integer                     |                                                                             |
| Float       | single precision floating point  |                                                                             |
| Double      | double precision floating point  |                                                                             |

## String Type
| Data Type | Name        | Explanation |
|:----------|:------------|:------------|
| String    | string type |             |

## Boolean Type
| Data Type    | Name         | Explanation                                                                   |
|:-------------|:-------------|:------------------------------------------------------------------------------|
| Boolean/Bool | Boolean type | The internal unified representation is Boolean, and Bool is the abbreviation  |

## Binary Type
| Data Type | Name        | Explanation                                            |
|:----------|:------------|:-------------------------------------------------------|
| Binary    | Binary type | In user layer, it is displayed as a hexadecimal string |

## Time Data Type
| Data Type |     | Name           | Explanation                                                                                                                                |
|:----------|:----|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| Datetime  |     | Data time type | In user layer, it is displayed in yyyy-MM-dd HH:mm:ss.SSS format                                                                           |
| Timestamp |     | Timestamp type | The underlying storage is of type Long, accurate to milliseconds, and the user layer is displayed in the format of yyyy-MM-dd HH:mm:ss.SSS |

## Generic Spatial Data Type
| Data Type          | Name                     | Explanation                                                                                                                                                                  |
|:-------------------|:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Geometry           | Generic Spatial type     | The parent type of all other space types. In the function, if the input is Geometry type, any space type can be input, and in user layer, it is displayed in the WKT format. |
| Point              | Point type               | In user layer, it is displayed in the WKT format                                                                                                                             |
| LineString         | Line type                | In user layer, it is displayed in the WKT format                                                                                                                             |
| Polygon            | Polygon type             | In user layer, it is displayed in the WKT format                                                                                                                             |
| MultiPoint         | Multiple Point type      | In user layer, it is displayed in the WKT format                                                                                                                             |
| MultiLineString    | Multiple LineString type | In user layer, it is displayed in the WKT format                                                                                                                             |
| MultiPolygon       | Multiple Polygon type    | In user layer, it is displayed in the WKT format                                                                                                                             |
| GeometryCollection | collection of geometries | In user layer, it is displayed in the WKT format                                                                                                                             |

## Customized ST-Application Data Types
| Data Type   | Name         | Explanation                                          |
|:------------|:-------------|:-----------------------------------------------------|
| Trajectory  | trajectory   | In user layer, it is displayed in the GeoJSON format |
| RoadSegment | Road segment | In user layer, it is displayed in the GeoJSON format |
| RoadNetwork | Road Network | In user layer, it is displayed in the geoJSON format |