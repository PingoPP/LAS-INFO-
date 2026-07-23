import os 
import sys

conda_env = os.path.dirname(sys.executable)
os.environ["TCL_LIBARY"] = os.path.join(conda_env, "Libary", "lib", "tcl8.6")
os.environ["TK_LIBRARY"] = os.path.join(conda_env, "Libary", "lib", "tk8.6")

print("Main imported")

from gui import create_gui 
from analysis import analyze_las
from tkinter import filedialog, messagebox
import tkinter as tk

def main(): 
    root = tk.Tk()
    root.withdraw()

    file_path = filedialog.askopenfilename(
        title="Select a .LAS / .LAZ file",
        filetypes=[("LAS/LAZ files", "*.las, *.laz")]
    )

    if not file_path:
        print("BAD BOY and GOTCHA!")
        return
    
    try: 
        stats = analyze_las(file_path)
    except Exception as e: 
        messagebox.showerror(f"Error:\n{e}")
        return
    
    root.destroy()
    create_gui(stats)

    if __name__ == "__main__":
        main()
