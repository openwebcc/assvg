# AsSVG-ArcGIS Geoprocessing script

The AsSVG-ArcGIS Geoprocessing script allows to export ArcGIS Point-, Line- or Polygon layers to SVG circle, text or path notation. You may export absolute or relative path d-attributes for Lines and Polygons as well as circles with cx, cy attributes when Relative-Coordinates is checked or text elements with x, y attributes when Relative-Coordinates is unchecked for Points. To reduce File size Coordinate-Precision can be defined. AsSVG does not export styles as set in ArcGIS but allows to specify an attribute via Class-Field that will be used for including classes in the output .svg. All attribute-data specified by Data-Field may be included via custom-namespaced SVG-attributes.

##Usage
Download the source, open asSVG-ArcGIS.1.0.tbx with ArcCatalog or add it to your Toolboxes in ArcMap. That's it, now you're ready to use it.

##Command line syntax
`asSVG <Layer> <Relative-Coordinates> {Coordinate-Precision} {Class-Field} {Data-Field_s_;Data-Field_s_...} <Output-SVG>`

##Parameters

###`<Layer>`
specify an ArcGIS Point, Line or Polygon layer

###`<Relative-Coordinates>`
set relative or absolute notation switch which will cause the following:
- Relative-Coordinates checked
  - Line- and Polygon-coordinates are expressed in relative moves from the starting coordinate. This may reduce file size in projected coordinate systems with big coordinates
  - Points are presented as circles with cx and cy coordinates
- Relative-Coordinates unchecked
  - Line- and Polygon-coordinates are expressed with absolute values
  - Points are presented as text-elements with x, y coordinates. Note: all attributes specified in Data-Field(s) will be used for the text-content

###{Coordinate-Precision}
set the number of digits right of the comma. e.g. 123456.87654321 with precision set to 1 will result in 123456.9

###{Class-Field}
use this field as class-attribute for styling. e.g. an attribute named 'type' with value 'road' in line layer roads will result in class='linroad'. `ply*`, `pnt*` and `txt*` prefixes are added to the corresponding layer types to guarantee unique classes. A CDATA section with default styles that may be modified later is added to the output .svg. Colors are defined through the [Tango-Palette](Tango-Palette.gpl) that comes with [Inkscape](http://inkscape.org).

###{Data-Field_s_;Data-Field_s_...}
specify all fields to be included as custom-namespaced attributes in the output .svg. e.g. attributes named id, title with values 123, 'Route 666' will be mapped to assvg:id='123' assvg:title='Route 66'.
Exporting points with Relative coordinates unchecked causes the contents of all datafield(s) to be written as text-elements.

###`<Output-SVG>`
set output .svg name here. Note: existing files can not be overwritten



####That's it. I hope you find this tool useful :)
