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
	@echo "=== Adding kernel for jupyter/lab"
	$(PYTHON) -m ipykernel install --user --name={{cookiecutter.project_name}}

setup_dev_env: Dockerfile docker-compose.yml
	@echo "=== Building development environment image"
	docker compose build dev
	@echo "=== Running development environment container"
	docker compose run --rm -dit deploy

deploy_app: Dockerfile docker-compose.yml
	@echo "=== Building development environment image"
	docker compose build dev
	@echo "=== Running development environment container"
	docker compose run --rm -dit deploy

clean:
	rm -rf __pycache__
	rm -rf $(VENV)

