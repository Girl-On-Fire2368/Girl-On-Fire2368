- Homework 2
!pip install matplotlib
!pip install tabulate
!pip install pydub
!pip install sounddevice
!pip install pya
!pip install astronify
!apt install -qq -y portaudio19-dev
!pip install pyaudio
!pip install sonipy

def calculate_free_fall(height, velocity):
    acceleration = 9.8
    time = math.sqrt(2 * height/acceleration)
    velocity_f = velocity + acceleration*time
    return time, velocity_f

input_D = int(input("How many inputs are you willing to matimaticulate? -- "))

time_l = []
velocity_f_l = []
position_l = []

print("ID\t \t\tHeight_i \t\tVelocity_i\t\tTime\t Velocity_f\tPosition")


for i in range(input_D):
    print(f"ID {i+1}:")

    height = float(input("Enter the initial height (in meters): "))
    velocity = float(input("Enter the initial velocity (in m/s): "))

    fall_time, velocity_f = calculate_free_fall(height, velocity)
    position = height - 0.5 * 9.8 * fall_time**2 #hence; s = h-1/2 at^2

    time_l.append(fall_time)
    velocity_f_l.append(velocity_f)
    position_l.append(position)

    print(f"{i+1}\t\t\t{height:.2f} m\t\t{velocity:.2f} m/s\t{fall_time:.2f} s\t{velocity_f:.2f} m/s\t\t{position:.2f} m")

t = sorted(zip(time_l, velocity_f_l, position_l), key=lambda x: x[0])
time_l, velocity_f_l, position_l = zip(*t)

plt.subplot(3, 1, 1)
plt.plot(time_l, velocity_f_l, color='#0fffff')
plt.title('Velocity • vs • Time')
plt.grid(True)

plt.subplot(3, 1, 2)
plt.plot(time_l, position_l, marker='x', color='#000fff')
plt.title('Position • v • Time')
plt.grid(False)

plt.tight_layout()

plt.show()


sorted_data = sorted(zip(time_l, velocity_f_l, position_l), key=lambda x: x[0])
time_l, velocity_f_l, position_l = zip(*sorted_data)

fig, axs = plt.subplots(3, 1, figsize=(10, 8))

def update(frame):
    axs[0].clear()
    axs[1].clear()

    for i in range(frame + 1):
        axs[0].plot(time_l[i], velocity_f_l[i], 'bx-', label='Velocity')
        axs[1].plot(time_l[i], position_l[i], 'ro-', label='Position')

    axs[0].set_title('Time • vs • Velocity')
    axs[0].set_xlabel('Time')
    axs[0].set_ylabel('Velocity')

    axs[1].set_title('Time • vs • Position')
    axs[1].set_xlabel('Time')
    axs[1].set_ylabel('Position')


frames = len(time_l)
animation = FuncAnimation(fig, update, frames=frames, interval=10000, repeat=True)




HTML(animation.to_jshtml()) Hi, I’m @Girl-On-Fire2368
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Girl-On-Fire2368/Girl-On-Fire2368 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
