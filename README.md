# Local Decision Model

A project exploring a ready-trained, configurable local decision model for ESP32-class devices and other small physical projects.

**Status: concept stage.** The first release is a theoretical concept paper. Model weights, a runnable implementation and measured hardware results are future work.

## Read the concept

[A Local Decision Model for Physical Projects (PDF)](docs/local-decision-model-concept.pdf)

The six-page paper describes the proposed interface, sensor pipeline, deployment options, resource constraints and a path toward making the system useful without asking every user to train a model.

## Core idea

```text
microphone / sensors
        ↓
input adapters and supported perception models
        ↓
local decision core
        ↓
structured event or answer
        ↓
your application's response
```

A project supplies observations and a bounded question or task. The proposed model returns a structured result that the application can act on: blink a light, change a toy's behavior, update an interface or send a local notification.

Sound recognition would initially depend on supported perception models. Recognizing arbitrary new sounds and understanding arbitrary task descriptions remain research questions. User-specific model training is deferred.

## Deployment

The model could share the main board when the complete project fits its memory and compute budget, or run on a companion module with a simple connection to the application board.

Additional storage can hold model assets, but it does not isolate runtime memory or processing demand. Each supported configuration will need measured resource requirements.

## Project direction

This repository is intended to grow with the project:

- `docs/`: the concept paper and, later, interface and deployment documentation
- `models/` (planned): model packages, model cards and evaluation results
- `src/` (planned): the decision interface, runtime integration and board adapters
- `examples/` (planned): complete microphone and sensor projects

The first practical milestone would be a small end-to-end example with a defined sound vocabulary, sensor inputs, structured outputs and a measured hardware budget.

## Ideas and suggestions

Use the repository's issues to suggest useful projects, sensor combinations, interface designs or implementation approaches. Concrete constraints and small examples are especially welcome.

## Inspiration

[Jev's state-and-typed-question interface](https://docs.typesafe.ai/introduction) is an inspiration for the decision interface. The local hardware architecture described here is an original proposal by ardchain.
