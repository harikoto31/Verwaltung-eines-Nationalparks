# Verwaltung eines Nationalparks

A desktop application for managing the staff, animals and trail network of a national park, built with C++ for the logic and the Qt framework for the GUI. It was one of my first projects combining a separate logic layer with a graphical interface, and it grew from simple lists into a small management tool with graph algorithms on the park's trail network.

- Manages three types of staff (rangers, administration, scientists) and three types of animals (mammals, birds, reptiles), each with their own attributes
- Adds and edits entries through dialogs for each type
- Filters the lists by type with checkboxes and shows all details of an entry as a tooltip on hover
- Sorts staff by personnel number, salary or distance to a reference salary, and animals by name, age or distance to a reference age, ascending or descending with a live preview
- Shows statistics such as endangered animals, predators, venomous reptiles or full-time staff
- Saves and loads both lists as JSON with nlohmann/json (earlier versions used a binary file and CSV)
- Draws the trail network as a map with locations and trails, loaded from JSON
- Blocks and unblocks trails, which then appear greyed out and are ignored by the algorithms below
- Marks every location reachable from a starting point with breadth-first search
- Finds the shortest route between two locations with Dijkstra's algorithm and highlights it in red along with the total distance
- Has a menu bar, toolbar, status bar messages, window modes and an exit confirmation, styled with a Qt stylesheet

The project is split into two qmake subprojects. The logic layer is a static library in pure C++ without any Qt dependency, and the GUI layer links against it. Staff and animals are built on the abstract base classes `Angestellter` and `Spezies`, whose virtual functions (`getInfo`, `toJson`, `ausgabeTooltip`) let the GUI treat every type the same way. The trail network is stored as a graph with an adjacency list, which both algorithms work on, while the map is drawn with `QGraphicsScene`.

Antsa Haritiana Ramparany, computer science student at Hochschule Darmstadt (h_da), Germany
