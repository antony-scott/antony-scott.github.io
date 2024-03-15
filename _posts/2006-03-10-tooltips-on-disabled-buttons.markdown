---
layout:     post
title:      Tooltips on disabled buttons
date:       2006-03-10
categories: WinForms
---
After searching the web quite extensively looking for a solution to this problem, I found many other people were having the same problem. But none had an answer, so after a few hours of hacking around I have managed to come up with a solution. It's not pretty (it uses win32 api calls), but it does the job.

```csharp
    int WM_MOUSEMOVE = 0x0200;

    [StructLayout(LayoutKind.Sequential)]
    public class POINT
    {
        public long  x;
        public long  y;
    }

    [DllImport("user32", CharSet=CharSet.Auto)]
    public static extern IntPtr SendMessage(IntPtr hWnd, int msg, int wParam, POINT lParam);
```

When a button is disabled it does not receive any mouse related messages. The parent of the button does receive them. So I put a MouseMove event handler in place for my form. I still use the standard Winforms tooltip control to hold the tooltip text for the button.

```csharp
    private void Form1_MouseMove(object sender, System.Windows.Forms.MouseEventArgs e)
    {
         Point pt = PointToClient(Cursor.Position);
         Control control = GetChildAtPoint(pt);
         if (control != null)
         {
            if (control is Button &amp;amp;&amp;amp; !control.Enabled)
            {
                string tip = toolTip1.GetToolTip(control);
                if (tip.Length > 0)
                {
                    POINT point = new POINT();
                    point.x = Cursor.Position.X;
                    point.y = Cursor.Position.Y;
                    SendMessage(control.Handle, (int) WindowsMessages.WM_MOUSEMOVE, 0, point);
                }
            }
        }
    }
```
This seems to work perfectly. Hope it helps someone else out.
