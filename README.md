# 🐦 Flappy Bird NEAT AI

Game Flappy Bird với AI tự học sử dụng thuật toán NEAT (NeuroEvolution of Augmenting Topologies) để train neural network chơi game.

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python)
![Pygame](https://img.shields.io/badge/Pygame-2.6-green?logo=pygame)
![NEAT](https://img.shields.io/badge/NEAT-AI-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 🎯 Tính năng

- ✅ Game Flappy Bird hoàn chỉnh với pygame
- 🧠 AI tự học chơi game bằng NEAT algorithm  
- 📊 Visualization training process và network
- 🎮 Pixel-perfect collision detection
- 📈 Tracking fitness scores qua các generation
- 🔄 Population evolution với genetic algorithm

## 🛠️ Tech Stack

- **Python 3.12+** - Ngôn ngữ lập trình chính
- **Pygame 2.6+** - Game development framework
- **NEAT-Python** - NeuroEvolution library
- **NumPy** - Numerical computing
- **Matplotlib** - Data visualization & plotting
- **Graphviz** - Network topology visualization

## 📁 Cấu trúc Project

```
flappy-bird-neat/
├── game/
│   ├── src/
│   │   └── flappy_bird.py      # Main game file với NEAT integration
│   ├── imgs/                   # Game assets (bird, pipe, background)
│   │   ├── bird1.png
│   │   ├── bird2.png  
│   │   ├── bird3.png
│   │   ├── pipe.png
│   │   ├── bg.png
│   │   └── base.png
│   └── visualize.py            # Visualization utilities
├── config-feedforward.txt     # NEAT configuration
├── requirements.txt           # Python dependencies
├── .gitignore                # Git ignore rules
└── README.md                 # Documentation
```

## 🚀 Installation & Setup

### 1. Clone Repository
```bash
git clone https://github.com/LeVietThanh1412/flappy-bird-neat.git
cd flappy-bird-neat
```

### 2. Tạo Virtual Environment
```bash
python -m venv flappy
source flappy/bin/activate  # Linux/Mac
# hoặc
flappy\Scripts\activate     # Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Tạo Game Assets (nếu chưa có)
```bash
python create_images.py
```

## 🎮 Cách chạy

### Chạy AI Training
```bash
cd flappy-bird-neat
python game/src/flappy_bird.py
```

### Thông số Training
- **Population Size**: 100 birds mỗi generation
- **Max Generations**: 50 
- **Fitness Function**: Thời gian sống + bonus vượt pipe
- **Neural Network**: 3 inputs → hidden nodes → 1 output
- **Selection**: Tournament selection với elitism

## 🧠 NEAT Algorithm

### Input Nodes (3):
1. **Bird Y Position** - Vị trí bird trên màn hình
2. **Distance to Top Pipe** - Khoảng cách đến pipe trên
3. **Distance to Bottom Pipe** - Khoảng cách đến pipe dưới

### Output Node (1):
- **Jump Decision** - Output > 0.5 → bird nhảy

### Fitness Function:
```python
fitness = time_alive * 0.1 + pipes_passed * 5 - collision_penalty
```

## 📊 Monitoring Training

Game hiển thị real-time:
- **Score**: Số pipe đã vượt qua
- **Generation**: Generation hiện tại  
- **Alive**: Số bird còn sống
- **Lines** (optional): Neural network decision lines

## ⚙️ Configuration

File `config-feedforward.txt` chứa các thông số NEAT:

```ini
[NEAT]
fitness_criterion     = max
fitness_threshold     = 100
pop_size              = 100
reset_on_extinction   = False

[DefaultGenome]
# Network parameters
num_inputs              = 3
num_outputs             = 1
initial_connection      = full_direct
feed_forward            = True
```

## 🔧 Customization

### Thay đổi khó độ game:
```python
# Trong flappy_bird.py
class Pipe:
    GAP = 200    # Khoảng cách giữa 2 pipe (càng nhỏ càng khó)
    VEL = 5      # Tốc độ pipe (càng lớn càng khó)
```

### Thay đổi bird physics:
```python
class Bird:
    MAX_ROTATION = 25    # Góc xoay tối đa
    ROT_VEL = 20        # Tốc độ xoay
    ANIMATION_TIME = 5   # Tốc độ animation
```

## 📈 Kết quả Training

Thường sau 10-20 generations:
- Birds học được cách tránh pipe cơ bản
- Fitness score tăng dần đều
- Xuất hiện những bird có thể vượt 10+ pipes

Sau 30-50 generations:
- AI có thể chơi indefinitely
- Neural network tối ưu topology
- Consistent high scores

## 🐛 Troubleshooting

### Lỗi không tìm thấy images:
```bash
mkdir -p game/imgs
python create_images.py
```

### Lỗi import modules:
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Performance issues:
- Giảm `pop_size` trong config
- Tắt visualization (`DRAW_LINES = False`)
- Giảm FPS (`clock.tick(30)` → `clock.tick(60)`)

## 📚 Tài liệu tham khảo

- [NEAT-Python Documentation](https://neat-python.readthedocs.io/)
- [Pygame Documentation](https://www.pygame.org/docs/)
- [NEAT Algorithm Paper](http://nn.cs.utexas.edu/downloads/papers/stanley.ec02.pdf)

## 🤝 Contributing

1. Fork repository
2. Tạo feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## 📝 License

Project này sử dụng MIT License. Xem file `LICENSE` để biết thêm chi tiết.

## 👨‍💻 Author

**Lê Việt Thành** - [@LeVietThanh1412](https://github.com/LeVietThanh1412)

---

⭐ Star repo nếu project hữu ích cho bạn!