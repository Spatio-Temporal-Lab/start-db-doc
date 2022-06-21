# START-DB拟支持的数据类型

## Numeric Data Type

| Express     | Name                             | Illustrate                                                                                |
|:------------|:---------------------------------|:------------------------------------------------------------------------------------------|
| Integer/Int | Integer                          | The internal unified representation is Integer, and Int is convenient for users to write  |
| Long        | long integer                     |                                                                                           |
| Float       | single precision floating point  |                                                                                           |
| Double      | double precision floating point  |                                                                                           |

## String Type
| Express | Name           | Illustrate |
|:--------|:---------------|:-----------|
| String  | Character type |            |

## Boolean Type
| Express      | Name         | Illustrate                                                                                 |
|:-------------|:-------------|:-------------------------------------------------------------------------------------------|
| Boolean/Bool | Boolean type | The internal unified representation is Boolean, and Bool is convenient for users to write  |

## Binary Type
| Express | Name        | Illustrate                                           |
|:--------|:------------|:-----------------------------------------------------|
| Binary  | Binary type | The user layer is displayed as a hexadecimal string  |

## Time Data Type
| Express   | Name           | Illustrate                                                                                                                                  |
|:----------|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| Datetime  | Time date type | The user layer is displayed in yyyy-MM-dd HH:mm:ss.SSS format                                                                               |
| Timestamp | Timestamp type | The underlying storage is of type Long, accurate to milliseconds, and the user layer is displayed in the format of yyyy-MM-dd HH:mm:ss.SSS  |

## Generic Spatial Data Type
| Express            | Name                 | Illustrate                                                                                                                                                            |
|:-------------------|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Geometry           | Space type           | The parent type of all other space types. In the function, if the input is Geometry type, any space type can be input, and the user layer is displayed in WKT format. |
| Point              | Point type           | User layer is displayed in WKT format                                                                                                                                 |
| LineString         | Line type            | User layer is displayed in WKT format                                                                                                                                 |
| Polygon            | Face type            | User layer is displayed in WKT format                                                                                                                                 |
| MultiPoint         | Multipoint type      | User layer is displayed in WKT format                                                                                                                                 |
| MultiLineString    | Multi-line type      | User layer is displayed in WKT format                                                                                                                                 |
| MultiPolygon       | faceted type         | User layer is displayed in WKT format                                                                                                                                 |
| GeometryCollection | collection of space  | User layer is displayed in WKT format                                                                                                                                 |

## Custom Spatial Data Types
| Express     | Name         | Illustrate                                 |
|:------------|:-------------|:-------------------------------------------|
| Trajectory  | Track        | User layer is displayed in GeoJson format  |
| RoadSegment | Road section | User layer is displayed in GeoJson format  |
| RoadNetwork | Road Network | User layer is displayed in GeoJson format  |