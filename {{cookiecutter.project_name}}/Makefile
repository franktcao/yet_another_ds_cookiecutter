VENV = .venv
PYTHON = $(VENV)/bin/python
PIP = $(VENV)/bin/pip

setup: requirements.txt
	@echo "=== Initializing git"
	git init
	@echo "=== Setting up and activating virtual environment"
	python -m venv $(VENV)
	source $(VENV)/bin/activate
	@echo "=== Installing packages"
	$(PIP) install --upgrade pip
	$(PIP) install -r requirements.txt
	poetry shell
	@echo "=== Installing pre-commit hooks"
	pre-commit install	
	@echo "=== Adding kernel for jupyter/lab"
	# $(PYTHON) -m ipykernel install --user --name={{cookiecutter.project_name}}

setup_dev_env: Dockerfile docker-compose.yml
	@echo "=== Building development environment image and run container in detached mode"
	docker compose up --build -d dev

setup_deploy_env: Dockerfile docker-compose.yml
	@echo "=== Building deploy environment image"
	docker compose build deploy --build-arg ENV=prod
	@echo "=== Running deploy environment container"
	docker compose run --rm -dit deploy

clean:
	rm -rf __pycache__
	rm -rf $(VENV)
	docker system prune

