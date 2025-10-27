# motopp
# ! NOT DONE YET !
## Description

# MotoPP - Motorcycle Management Application

A web-based application for motorcycle enthusiasts to manage their bikes and access the marketplace. Built with Flask and MySQL, containerized with Docker.

## Features

- User authentication (signup/login)
- Personal motorcycle management
- Motorcycle marketplace
- Parts scraper integration
- Responsive web interface

## Tech Stack

- **Backend**: Python/Flask
- **Database**: MySQL 8.0
- **Frontend**: HTML/CSS
- **Containerization**: Docker
- **Development Tools**: Docker Compose

## Project Structure

```
.
├── docker-compose.yaml          # Docker Compose configuration
├── motopp/                     # Main application directory
│   ├── Dockerfile             # Application container configuration
│   ├── requirements.txt       # Python dependencies
│   ├── main.py               # Main application logic
│   ├── auth.py               # Authentication handling
│   ├── models.py             # Database models
│   └── templates/            # HTML templates
├── mysql/                     # MySQL configuration
│   ├── Dockerfile            # Database container configuration
│   └── database_motopp.sql   # Initial database schema
└── parts_scraper/            # Parts scraping module
    ├── requirements.txt      # Scraper dependencies
    └── setup.py             # Scraper setup configuration
```

## Getting Started

### Prerequisites

- Docker
- Docker Compose
- Git

### Installation

1. Clone the repository:
```bash
git clone [repository-url]
cd motopp
```

2. Create and configure the environment file:
```bash
touch .env
```

3. Add the following configurations to the `.env` file:
```bash
SECRET_KEY=your_secret_key
MYSQL_HOST=your_mysql_localhost
MYSQL_USER=your_mysql_user
MYSQL_PASSWORD=your_mysql_password
```

4. Start the application:
```bash
docker-compose up --build -d
```

5. Access the application:
- Open your browser and navigate to `http://localhost:5000`
- Create a new account or log in with existing credentials

## Development

To set up the development environment:

1. Create a Python virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
cd motopp
pip install -r requirements.txt
```

3. Run the application in development mode:
```bash
python run.sh
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support, please open an issue in the GitHub repository or contact the maintainers.
