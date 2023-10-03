## Autonomous Driving Stack: Interaction Diagram

```mermaid
graph TD
    subgraph Autonomous Car System
        LIDAR[(LIDAR Sensor)]

        CORE[Core Container]
        PERCEPTION[Perception Container]
        ODOMETRY[Odometry Container]
        FUNCTION[Function Container]

        LIDAR -->|UDP LIDAR Packets| CORE
        CORE -.->|Processed LIDAR Data<br>[View Interface](https://github.com/Darainer/Mermaid_Markdown_C4_style/blob/main/core_to_perception_interface.hpp)| PERCEPTION
        CORE -.->|Processed LIDAR Data<br>[View Interface](https://github.com/Darainer/Mermaid_Markdown_C4_style/blob/main/core_to_odometry_interface.hpp)| ODOMETRY

        PERCEPTION -. "Tracked Object List<br>[View Interface](https://github.com/Darainer/Mermaid_Markdown_C4_style/blob/main/perception_to_function_objects_interface.hpp)" .-> FUNCTION
        PERCEPTION -. "Road Lane Outputs<br>[View Interface](https://github.com/Darainer/Mermaid_Markdown_C4_style/blob/main/perception_to_function_lanes_interface.hpp)" .-> FUNCTION
        PERCEPTION -. "Occupancy Grid<br>[View Interface](https://github.com/Darainer/Mermaid_Markdown_C4_style/blob/main/perception_to_function_grid_interface.hpp)" .-> FUNCTION

        ODOMETRY -->|6 DOF Odometry Pose<br>[View Interface](https://github.com/Darainer/Mermaid_Markdown_C4_style/blob/main/odometry_to_function_interface.hpp)| FUNCTION
    end
