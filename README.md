# song-vibe-matcher-
import tkinter as tk
import random
import webbrowser

# Mood-song mapping with real Spotify track URLs (double-checked ✅)
songs_by_mood = {
    "happy": [
        ("Happy – Pharrell Williams", "https://open.spotify.com/track/60nZcImufyMA1MKQY3dcCH"),
        ("Uptown Funk – Mark Ronson ft. Bruno Mars", "https://open.spotify.com/track/32OlwWuMpZ6b0aN2RZOeMS"),
        ("On Top of the World – Imagine Dragons", "https://open.spotify.com/track/2vwlzO0Qp8kfEtzTsCXfyE")
    ],
    "sad": [
        ("Let Her Go – Passenger", "https://open.spotify.com/track/3JvrhDOgAt6p7K8mDyZwRd"),
        ("Someone Like You – Adele", "https://open.spotify.com/track/4kflIGfjdZJW4ot2ioixTB"),
        ("Arcade – Duncan Laurence", "https://open.spotify.com/track/6mTJK3kaXbGg0zj6hXkZ8o")
    ],
    "chill": [
        ("Sunflower – Post Malone", "https://open.spotify.com/track/3KkXRkHbMCARz0aVfEt68P"),
        ("Kesariya – Arijit Singh", "https://open.spotify.com/track/0JhivpP4kzPpXzt7LRYj3P"),
    
    ],
    "love": [
        ("Perfect – Ed Sheeran", "https://open.spotify.com/track/0tgVpDi06FyKpA1z0VMD4v"),
        ("Raataan Lambiyan – Jubin Nautiyal", "https://open.spotify.com/track/3FAJ6O0NOHQV8Mc5Ri6ENp"),
        ("Talking to the Moon – Bruno Mars", "https://open.spotify.com/track/0ByMNEPAPpOR5H69yu0R6C")
    ],
    "motivated": [
        ("Believer – Imagine Dragons", "https://open.spotify.com/track/0pqnGHJpmpxLKifKRmU6WP"),
        ("Zinda – Bhaag Milkha Bhaag", "https://open.spotify.com/track/5uH2zAv4PQ2YkZHLrf1LwT"),
        ("Apna Time Aayega – Gully Boy", "https://open.spotify.com/track/1rgnBhdG2JDFTbYkYRZAku")
    ]
}

# Function to display the song
def show_song(mood):
    song, link = random.choice(songs_by_mood[mood])
    result_label.config(text=f"🎧 Your Song: {song}")
    link_label.config(text="🎵 Click here to open on Spotify", fg="blue", cursor="hand2")
    link_label.bind("<Button-1>", lambda e: webbrowser.open(link))
    link_label.pack(pady=10)

# GUI setup
root = tk.Tk()
root.title("🎶 Song Vibe Matcher")
root.geometry("400x450")
root.config(bg="#fcefee")

# Title
tk.Label(root, text="Choose Your Mood 🎧", font=("Helvetica", 16, "bold"), bg="#fcefee", fg="#333").pack(pady=20)

# Mood buttons
moods = ["happy", "sad", "chill", "love", "motivated"]
for mood in moods:
    tk.Button(root, text=mood.capitalize(), width=20, bg="#ffb6c1", fg="#000", font=("Arial", 12),
              command=lambda m=mood: show_song(m)).pack(pady=5)

# Result label
result_label = tk.Label(root, text="", font=("Arial", 12, "italic"), bg="#fcefee", fg="#444")
result_label.pack(pady=20)

# Link label (clickable Spotify)
link_label = tk.Label(root, text="", font=("Arial", 12, "underline"), bg="#fcefee")
link_label.pack()

root.mainloop()

