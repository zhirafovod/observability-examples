SOLUTION_NAME := ${USER}malware

# Define a default goal.
default: test


clean:
	@test -d ./"${SOLUTION_NAME}" && rm -r ./"${SOLUTION_NAME}" || echo "nothing to clean"

# Validate target to check solution files are correct.
fork: clean
	@echo "forking solution..."
	fsoc solution fork --source-dir=package ${SOLUTION_NAME} --verbose
	@echo "Solution forked."


# Validate target to check solution files are correct.
.PHONY: validate
validate: fork
	@echo "Validating solution..."
	fsoc solution validate --directory ${SOLUTION_NAME} --tag=base -v
	@echo "Solution validated."

# Push target to deploy your solution.
push:
	@echo "Pushing solution..."
	fsoc solution push --directory ${SOLUTION_NAME} --tag=base
	@echo "Solution pushed."

# Test target that needs to run fork and local validation
test:
	@echo "to be implemented"

lint: markdown-lint

markdown-lint:
	@echo "Running markdown lint..."
	markdownlint *.md
	@echo "Completed markdown lint."

# Test which require fsoc tenant set up
integration_test: validate
	@echo "Running integration tests..."
	@test -d ./"${SOLUTION_NAME}" && rm -r ./"${SOLUTION_NAME}" || echo "nothing to clean"
	@echo "Completed integration tests."
