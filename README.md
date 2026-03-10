# myclashrule
自用的openclahs规则
graph TD
    %% Define styles for different materials
    classDef metal fill:#f2f2f2,stroke:#666,stroke-width:2px,rx:5,ry:5;
    classDef roller fill:#b3d9ff,stroke:#005cbf,stroke-width:2px;
    classDef base fill:#d9d9d9,stroke:#666,stroke-width:1px,stroke-dasharray: 5 5;
    classDef paper fill:#ffcccc,stroke:#cc0000,stroke-width:1px;

    subgraph "Overall Structure (Isometric View)"
        A[U型不锈钢支架<br>(304材质)]:::metal -->|固定| B[厚重底座<br>(建议金属或吸盘)]:::base;
        
        %% Rollers
        SubAxle1[主导向轴<br>(直径20mm 不锈钢管)]:::roller;
        SubAxle2[剥离细轴<br>(直径8mm 精光滑杆)]:::roller;
        SubAxle3[压纸轴<br>(带防滑橡胶套)]:::roller;

        A --- SubAxle1;
        A --- SubAxle2;
        A --- SubAxle3;
        
        %% Connections and placement
        link1[主导向轴] -- "放置于前方" -- SubAxle1;
        link2[剥离细轴] -- "放置于主轴下方/后方" -- SubAxle2;
        link3[压纸轴] -- "压在主轴上方" -- SubAxle3;
        
        %% Labels for context
        TextA3[A3平张标签纸从此处插入] --> SubAxle1;
        TextPop[标签在此处弹起] --> SubAxle2;
        TextPull[手动向下/向后拉动底纸] --> SubAxle2;
    end

    subgraph "Working Principle (Side Sectional View)"
        
        %% Core components
        R1((Main<br>Roller<br>Φ20mm)):::roller;
        R2((Peeling<br>Bar<br>Φ8mm)):::roller;
        P_Bar((Pressure<br>Bar)):::roller;

        %% Paper Path
        Feed[A3平张纸输入] ==> R1;
        R1 --> Pass[底纸贴着大轴移动];
        
        %% Sharp angle creation
        SharpAngle{转折角<br>&gt;130度}:::paper;
        Pass ==> R2:::paper;
        
        %% Label ejection
        Label[<b style='color:red;'>标签纸</b>由于刚性<br><b style='color:red;'>自然弹起</b>];
        Pass -.-> Label:::paper;
        
        %% Bottom Liner movement
        Liner[<b style='color:blue;'>底纸</b>被拉动<br>贴着细轴]:::paper;
        R2 ==> Liner:::paper;
        PullDir(手动拉动方向) == Liner;
        
        %% Relate parts
        Feed -.-> P_Bar;
        P_Bar -- "增加静摩擦<br>防止打滑" --> R1;
    end
