# Exercism Test Runner Template

This repository is a [template repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-template-repository) for creating [test runners][test-runners] for [Exercism][exercism] tracks.

1. Build the test runner, conforming to the [Test Runner interface specification](https://github.com/exercism/docs/blob/main/building/tooling/test-runners/interface.md).
   - Update the files to match your track's needs. At the very least, you'll need to update `bin/run.sh`, `Dockerfile` and the test solutions in the `tests` directory
   - Tip: look for `TODO:` comments to point you towards code that need updating
   - Tip: look for `OPTIONAL:` comments to point you towards code that _could_ be useful
   - Tip: if it proves impossible for the Docker image to work on a read-only filesystem, feel free to remove the `--read-only` flag from the `bin/run-in-docker.sh` and `bin/run-tests-in-docker.sh` files.
     At the moment, we don't yet enforce a read-only file system in the future, but we might in the future!
1. Remove the "Exercism Test Runner Template" section (this line and its preceding lines) from the `README.md` file

# Exercism Fake Test Runner

The Docker image to automatically run tests on Fake solutions submitted to [Exercism].

## Run the test runner

To run the tests of an arbitrary exercise, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run.sh <exercise-slug> <solution-dir> <output-dir>`

Once the test runner has finished, its results will be written to `<output-dir>/results.json`.

## Run the test runner on an exercise using Docker

_This script is provided for testing purposes, as it mimics how test runners run in Exercism's production environment._

To run the tests of an arbitrary exercise using the Docker image, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run-in-docker.sh <exercise-slug> <solution-dir> <output-dir>`

Once the test runner has finished, its results will be written to `<output-dir>/results.json`.

## Run the tests

To run the tests to verify the behavior of the test runner, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run-tests.sh`

These are [golden tests][golden] that compare the `results.json` generated by running the current state of the code against the "known good" `tests/<test-name>/results.json`. All files created during the test run itself are discarded.

When you've made modifications to the code that will result in a new "golden" state, you'll need to update the affected `tests/<test-name>/expected_results.json` file(s).

## Run the tests using Docker

_This script is provided for testing purposes, as it mimics how test runners run in Exercism's production environment._

To run the tests to verify the behavior of the test runner using the Docker image, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run-tests-in-docker.sh`

These are [golden tests][golden] that compare the `results.json` generated by running the current state of the code against the "known good" `tests/<test-name>/results.json`. All files created during the test run itself are discarded.

When you've made modifications to the code that will result in a new "golden" state, you'll need to update the affected `tests/<test-name>/expected_results.json` file(s).

[test-runners]: https://github.com/exercism/docs/tree/main/building/tooling/test-runners
[golden]: https://ro-che.info/articles/2017-12-04-golden-tests
[exercism]: https://exercism.io
