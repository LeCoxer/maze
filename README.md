import tkinter as tk
import random


window = tk.Tk()
window.geometry("1500x900")
window.title("maze of faun")
canvas = tk.Canvas(window, width=1500, height=900)
canvas.pack()

maze = [[], []]


def greenWall(q, e):
    maze[q][e] = 1
    canvas.create_rectangle(q * 50, e * 50, (q + 1) * 50, (e + 1) * 50, fill="green")


for i in range(100):
    for j in range(100):
        maze.append(0)
        canvas.create_rectangle(i * 50, j * 50, (i + 1) * 50, (j + 1) * 50, fill="grey")

for i in range(30):
    for j in range(30):
        greenWall(random.randint(0, 50), random.randint(0, 50))

canvas.create_rectangle(850, 450, 900, 400, fill="grey")
canvas.create_oval(850, 450, 900, 400, fill="gold")
canvas.create_rectangle(0, 0, 50, 50, fill="red", tag="hero")


def go(dx, dy):
    canvas.move("hero", dx, dy)


window.bind("<d>", lambda event: go(50, 0))
window.bind("<a>", lambda event: go(-50, 0))
window.bind("<s>", lambda event: go(0, 50))
window.bind("<w>", lambda event: go(0, -50))
window.mainloop()
