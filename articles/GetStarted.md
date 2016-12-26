# Program structure

__Program.cs__

```cs
using System;
using ImGui;

namespace EmptyTemplate
{
    class Program
    {
        [STAThread]
        static void Main()
        {
            Application.Run(new MainForm());
        }
    }
}
```

__MainForm.cs__

```cs
using ImGui;

namespace EmptyTemplate
{
    public class MainForm : Form
    {
        public MainForm() : base(new Rect(400, 300, 250, 450))
        {
        }

        protected override void OnGUI()
        {
            // your GUI code
        }
    }
}
```

# Hello ImGui

The Hello Wolrd Program of ImGui.

In MainForm.cs, override method OnGui:

```cs
    protected override void OnGUI()
    {
        GUI.Label(new Rect(0, 0, 100, 30), "Hello ImGui", "helloLabel");
    }
```

Result:

![Hello World Preview](../images/hello_world_preview.png)
