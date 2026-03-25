
import tkinter as tk
import random

def detect_overthinking(text):
    keywords_high = ["what if", "why", "maybe", "nervous", "overthinking", "fear", "anxious" ,"insecurity","stress","emotion"]
    keywords_medium = ["think", "confused", "not sure","worried","doubt"]

    score = 0

    for word in keywords_high:
        if word in text.lower():
            score += 2

    for word in keywords_medium:
        if word in text.lower():
            score += 1

    if score >= 4:
        return "HIGH 😵", random.choice(high_advice)
    elif score >= 2:
        return "MEDIUM 😐", random.choice(medium_advice)
    else:
        return "LOW 😌", random.choice(low_advice)

high_advice = [
    "You are overthinking. Take a deep breath.",
    "Not everything needs an answer right now.",
    "Relax. Your mind is creating stories.",
    "stop analysing the situation repeateadly.",
]

medium_advice = [
    
"Calm down—your overthinking is faster than their typing speed 😂💭📱",
    "Eat five star do nothing",
]

low_advice = [
    "You are doing good 👍",
    "Stay calm and positive.",
    "No overthinking detected 😄",
    "spend time with family.",
]

def analyze():
    text = entry.get("1.0", tk.END)
    level, advice = detect_overthinking(text)

    result_label.config(text=f"Overthinking Level: {level}")
    advice_label.config(text=f"Advice: {advice}")

root = tk.Tk()
root.title("Overthinking Detector 🧠")
root.geometry("400x400")
root.configure(bg="#1e1e1e")

title = tk.Label(root, text="Overthinking Detector", font=("Arial", 16, "bold"), fg="white", bg="#1e1e1e")
title.pack(pady=10)

entry = tk.Text(root, height=5, width=40)
entry.pack(pady=10)

analyze_btn = tk.Button(root, text="Analyze Thought", command=analyze, bg="#4CAF50", fg="white")
analyze_btn.pack(pady=10)

result_label = tk.Label(root, text="", font=("Arial", 12), fg="yellow", bg="#1e1e1e")
result_label.pack(pady=5)

advice_label = tk.Label(root, text="", font=("Arial", 10), fg="lightgreen", bg="#1e1e1e", wraplength=300)
advice_label.pack(pady=5)

root.mainloop()
