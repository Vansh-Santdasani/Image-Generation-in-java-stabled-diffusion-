![WhatsApp Image 2024-01-14 at 12 41 10 PM](https://github.com/Vansh-Santdasani/Image-Generation-in-java-stabled-diffusion-/assets/156500918/906681fc-432b-43e0-9646-f7bc14ce30d9)
![WhatsApp Image 2024-01-14 at 12 41 10 PM1](https://github.com/Vansh-Santdasani/Image-Generation-in-java-stabled-diffusion-/assets/156500918/b147154a-1814-4b58-a9fc-f45d1540f409)
![WhatsApp Image 2024-01-14 at 12 41 10 PM2](https://github.com/Vansh-Santdasani/Image-Generation-in-java-stabled-diffusion-/assets/156500918/a2992498-1227-45d9-9af4-75bbe5eed17a)
![3](https://github.com/Vansh-Santdasani/Image-Generation-in-java-stabled-diffusion-/assets/156500918/87889491-0726-48f4-b6a3-4feb91aabac0)
![4](https://github.com/Vansh-Santdasani/Image-Generation-in-java-stabled-diffusion-/assets/156500918/118d5948-462d-4d28-8fbf-c224edceacd0)

Certainly! Writing a README for a project is crucial for providing clear guidelines and information to users and contributors. Below is a sample README for your Stable Diffusion Image Generation project in Java:

---

# Stable Diffusion Image Generation

## Overview

Welcome to the Stable Diffusion Image Generation project in Java! This project demonstrates the implementation of a stable diffusion model for image generation using the [Deep Java Library (DJL)](https://djl.ai/).

## Table of Contents

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [StableDiffusionModel](#stablediffusionmodel)
  - [ImageEncoder](#imageencoder)
  - [TextEncoder](#textencoder)
- [Contributing](#contributing)
- [License](#license)

## Getting Started

### Prerequisites

- Java Development Kit (JDK) 8 or later
- Maven (for building and dependencies)
- DJL (please refer djl documentation to set it up)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/stable-diffusion-java.git
   cd stable-diffusion-java
   ```

2. Build the project using Maven:

   ```bash
   mvn clean install
   ```

## Usage

### StableDiffusionModel

The `StableDiffusionModel` class is the main entry point for image generation. To use it, initialize an instance by specifying the device (CPU or GPU):

```java
Device device = Device.gpu(); // or Device.cpu()
StableDiffusionModel model = new StableDiffusionModel(device);
```

#### Image Generation from Text

```java
String prompt = "A beautiful landscape";
int steps = 10;
Image generatedImage = model.generateImageFromText(prompt, steps);
generatedImage.getTransform().showImage(generatedImage);
```

#### Image Generation from Image

```java
String prompt = "A beautiful landscape";
Image referenceImage = Image.create(new File("path/to/reference/image.jpg"));
int steps = 10;
Image generatedImage = model.generateImageFromImage(prompt, referenceImage, steps);
generatedImage.getTransform().showImage(generatedImage);
```

### ImageEncoder

The `ImageEncoder` class translates `Image` objects into `NDArray` representations suitable for the stable diffusion model.

```java
int height = 512;
int width = 512;
ImageEncoder imageEncoder = new ImageEncoder(height, width);

Image inputImage = Image.create(new File("path/to/input/image.jpg"));
NDArray encodedImage = imageEncoder.processInput(null, inputImage).singletonOrThrow();
```

### TextEncoder

The `TextEncoder` class translates text prompts into `NDList` representations for the stable diffusion model.

```java
TextEncoder textEncoder = new TextEncoder();

String prompt = "A beautiful landscape";
NDList encodedText = textEncoder.processInput(null, prompt);
```

