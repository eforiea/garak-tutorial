# Quick Start: Running a Garak Scan

**1. Configure the Target**

In your YAML configuration file, specify the model endpoint and model name.

For example:

```yaml
plugins:
  target_type: openai.OpenAICompatible
  target_name: google/gemma-4-e2b
  generators:
    openai:
      OpenAICompatible:
        uri: http://localhost:1234/v1/
        max_tokens: 150
        temperature: 0.7
```

Replace `uri` with your model API endpoint and `target_name` with the model identifier expected by your API server.


Set your api key:

Powershell:
```powershell
$env:OPENAICOMPATIBLE_API_KEY="YOUR_API_KEY"
```

Bash:
```bash
export OPENAICOMPATIBLE_API_KEY="YOUR_API_KEY"
```

**2. Select a Probe**

Choose the security test you want to run:

```yaml
run:
  spec:
    include:
      - probes.grandma.Substances
```

Replace the probe name with the test you want to execute.

**3. Select a Detector**

Choose a detector compatible with your selected probe. Detectors evaluate model responses for specific behaviors or patterns. Configure the detector using the appropriate options supported by your Garak version and probe.

**4. Run the Scan**

Save the configuration as `config.yaml`, then run:

```bash
garak --config config.yaml
```

**5. Review the Results**

Inspect the generated report, review detector findings, and manually verify suspicious results before treating them as confirmed vulnerabilities.

**Important:** A detector match is an indication that requires investigation, not proof of a security vulnerability.