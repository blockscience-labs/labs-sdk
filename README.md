# BlockScience Labs SDK (Python)

## API

### Client
To utilize the BlockScience Labs SDK, you'll first need to create a client and authenticate it with the Labs platform. Once authenticated, the client can be used to interact, freely.

```python
from blocksciencelabs import Client

labs = Client({"LABS_EMAIL": "example@example.com", "LABS_PASS": "MyExamplePassword123"})
```
**Notes**: To authenticate, you'll need to pass a configuration object (dictionary) with both `LABS_EMAIL` and `LABS_PASS` as properties. Alternatively, you may set environment variables (named the same thing) in order to authenticate without being explicite -- this allows for safe sharing of code without fear of leaking private credentials.

**More Notes**: On the BlockScience Labs platform you will not need to authenticate at all. Authentication is handled for you ahead of time so you can simply instantiate a client and start utilizing the API immediately thereafter.

Example usage where authentication is handled via the Labs platform or environment variables:
```python
labs = Client()

labs.fetch_results(...)
```

#### Client.fetch_results(simulation_id)
`fetch_results` takes a single parameter -- a simulation ID -- and returns the raw results.

Example:
```python
results = labs.fetch_results(123)
df = pandas.DataFrame(results)
```

#### Client.import_results(csv_file_name, simulation_id)
Similar to `fetch_results`, `import_results` returns unserialized results from an exported result set that was downloaded by the user via the Labs UI. This method takes two parameters, the first being the path and file name of the CSV containing our results and the second being the simulation ID corresponding to the simulation responsible for generating the data on the Labs platform.

```python
results = labs.import_results("simulation.csv", 123)
df = pandas.DataFrame(results)
```
