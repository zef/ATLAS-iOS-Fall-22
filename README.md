# ATLAS iOS Fall 2022

My version of the student class repo.

## App Idea

An app that records and organizes measurements.


Take measurements of an object. Each object can have multiple dimensions, perhaps named by convention d1, d2, d3, but able to be renamed through some quick options (like width/length/height/depth).

Dimensions can be made in all types of units. Length, Weight, Volume, etc.

- Units can be converted
- Maybe some math can be done on these units?
  - Like the Soulver app?
- Dimension groups can be exported

Dimensions could be grouped into collections.


### Goals:

Quick and efficient data entry.

It would be easy to make an app like this that is tedious to use and
frustrating enough that it just isn't used.

Must be easier than jotting down in a note.

Heirarchy and features must not get in the way.

## Use Cases:

- 3d modeling: take the dimensions and record them using the app, then export or
transfer them to your modeling program.

- Construction, home maintenance, general use: record the sizes of things that
you are working with.
  - Door dimensions
  - Furniture dimensions
  - Parts, like plumbing fixture sizes, etc.

- Cars, bikes, hobbies, etc.
  - Wheel/tire sizes
  - Windshield wiper sizes

Exportable:

```
// Human readable format:
length: 18"
diameter: 14mm

// code format, for OpenSCAD:

inch = 25.4;
length = 18 * inch;
Diameter = 14;
```

Exportable as something usable in code, like OpenSCAD formats.


# Data Modeling:

- UnitType: Weight, length, volume, etc.
- Unit:
  - Options defined by UnitType
  - gram, lbs, etc.

- Collection: Parent type where we can
  - Object
    - Measurement:
      - name
      - unit
      - value
      - can convert between different units of the same UnitType

### Frameworks

https://developer.apple.com/documentation/foundation/units_and_measurement/

### Interface ideas:

When selecting a unit, display a grid of unit options.
  - Not everyone is working with the same types of units.
    - Previously-used dimensions should be prioritized
  - How should this be ordered?
    - Most common dimensions, or alphabetically?

    I think I'd like to provide some obvious/common units first, followed by
    some other logically-organized or alphabetical list. Previously-used
    dimensions prioritized.

When selecting unit, do you have to select the type first, or do we expose some
units directly at the top-level?

### Questions

- Is there a format that you can use to import parameters into Fusion360?
  - SolidWorks?
  - What other modeling programs?

  https://knowledge.autodesk.com/support/fusion-360/learn-explore/caas/sfdcarticles/sfdcarticles/How-to-import-excel-spreadsheets-into-Fusion-360-as-parameters.html

- How do we assist the user in whatever ways are possible:
  - without overcomplicating the interface
  - without creating a burden of defining all sorts of types

- What is a good interface for dealing with entry of:
    Feet, Inches, Fractional Inches. This is often frustrating and I haven't
    used a good UI for it.

### App Name Ideas

- Measurements
- Dimensions

### Non-Obvious Units

I'm not sure if it makes sense to do anything special with these. Might be
really cool to include some, but tedious to include many, and you won't ever
please everyone. Probably not worth it unless there is some traction, or I find
it personally useful. A plain-text "custom" field would probably cover most
usecases, no need for unit conversions with these, so proper types are less
valuable.

- Screw thread sizes: metric and SAE
- Electric wire gauges
- Bike Tire sizes

