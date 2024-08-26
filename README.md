# VehicleVanguard

## Introduction

**VehicleVanguard** is a command-line application built using TypeScript that allows users to create and manage different types of vehicles (Cars, Trucks, and Motorbikes). Users can interact with the application to create vehicles, perform various actions, and even have trucks tow other vehicles.

## Features

- Create different types of vehicles: Car, Truck, Motorbike.
- Perform actions like starting, stopping, accelerating, decelerating, turning, reversing, etc.
- Specific actions for each vehicle type, such as towing for trucks and doing a wheelie for motorbikes.

## Setup Instructions

1. **Clone the Repository**:

    ```bash
    git clone git@github.com:Moosorkh/vehiclevanguard.git
    cd VehicleVanguard
    ```

2. **Install Dependencies**:

    ```bash
    npm install
    ```

3. **Build the Project**:

    ```bash
    npm run build
    ```

4. **Run the Application**:

    ```bash
    npm start
    ```

## Code Examples

Below are some of the key changes made in the project:

### 1. Constructor in `Cli.ts` Updated to Accept a Single Array of Vehicles

```typescript
createCar(): void {
    inquirer.prompt([
        {
            type: 'input',
            name: 'color',
            message: 'Enter Color',
        },
        // other prompts...
    ]).then((answers) => {
        const car = new Car(
            Cli.generateVin(),
            answers.color,
            answers.make,
            answers.model,
            parseInt(answers.year),
            parseInt(answers.weight),
            parseInt(answers.topSpeed),
            []
        );
        this.vehicles.push(car);
        this.selectedVehicleVin = car.vin;
        this.performActions();
    });
}
```

### 2. Method to Create a New Car in Cli.ts
```typescript
createCar(): void {
    inquirer.prompt([
        {
            type: 'input',
            name: 'color',
            message: 'Enter Color',
        },
        // other prompts...
    ]).then((answers) => {
        const car = new Car(
            Cli.generateVin(),
            answers.color,
            answers.make,
            answers.model,
            parseInt(answers.year),
            parseInt(answers.weight),
            parseInt(answers.topSpeed),
            []
        );
        this.vehicles.push(car);
        this.selectedVehicleVin = car.vin;
        this.performActions();
    });
}
```
### 3. Method to Perform Actions on Selected Vehicles in Cli.ts
```typescript
performActions(): void {
    inquirer.prompt([
        {
            type: 'list',
            name: 'action',
            message: 'Select an action',
            choices: [
                'Print details',
                'Start vehicle',
                // other actions...
                'Tow a vehicle',
                'Do a wheelie',
                'Exit',
            ],
        },
    ]).then((answers) => {
        // code to handle each action...
        if (answers.action === 'Tow a vehicle' && vehicle instanceof Truck) {
            this.findVehicleToTow(vehicle);
            return;
        } else if (answers.action === 'Do a wheelie' && vehicle instanceof Motorbike) {
            (vehicle as Motorbike).wheelie();
        }
        // other conditions...
    });
}
```

### 4. Method to Create a New Car
```typescript
createCar(): void {
    inquirer.prompt([
        {
            type: 'input',
            name: 'color',
            message: 'Enter Color',
        },
        {
            type: 'input',
            name: 'make',
            message: 'Enter Make',
        },
        {
            type: 'input',
            name: 'model',
            message: 'Enter Model',
        },
        {
            type: 'input',
            name: 'year',
            message: 'Enter Year',
        },
        {
            type: 'input',
            name: 'weight',
            message: 'Enter Weight',
        },
        {
            type: 'input',
            name: 'topSpeed',
            message: 'Enter Top Speed',
        },
    ]).then((answers) => {
        const car = new Car(
            Cli.generateVin(),
            answers.color,
            answers.make,
            answers.model,
            parseInt(answers.year),
            parseInt(answers.weight),
            parseInt(answers.topSpeed),
            []
        );
        this.vehicles.push(car);
        this.selectedVehicleVin = car.vin;
        this.performActions();
    });
}
```
### 5. Method to Create a New Truck
```typescript
createTruck(): void {
    inquirer.prompt([
        {
            type: 'input',
            name: 'color',
            message: 'Enter Color',
        },
        {
            type: 'input',
            name: 'make',
            message: 'Enter Make',
        },
        {
            type: 'input',
            name: 'model',
            message: 'Enter Model',
        },
        {
            type: 'input',
            name: 'year',
            message: 'Enter Year',
        },
        {
            type: 'input',
            name: 'weight',
            message: 'Enter Weight',
        },
        {
            type: 'input',
            name: 'topSpeed',
            message: 'Enter Top Speed',
        },
        {
            type: 'input',
            name: 'towingCapacity',
            message: 'Enter Towing Capacity',
        },
    ]).then((answers) => {
        const truck = new Truck(
            Cli.generateVin(),
            answers.color,
            answers.make,
            answers.model,
            parseInt(answers.year),
            parseInt(answers.weight),
            parseInt(answers.topSpeed),
            [],
            parseInt(answers.towingCapacity)
        );
        this.vehicles.push(truck);
        this.selectedVehicleVin = truck.vin;
        this.performActions();
    });
}
```
### 6. Method to Create a New Motorbike
```typescript
createMotorbike(): void {
    inquirer.prompt([
        {
            type: 'input',
            name: 'color',
            message: 'Enter Color',
        },
        {
            type: 'input',
            name: 'make',
            message: 'Enter Make',
        },
        {
            type: 'input',
            name: 'model',
            message: 'Enter Model',
        },
        {
            type: 'input',
            name: 'year',
            message: 'Enter Year',
        },
        {
            type: 'input',
            name: 'weight',
            message: 'Enter Weight',
        },
        {
            type: 'input',
            name: 'topSpeed',
            message: 'Enter Top Speed',
        },
        {
            type: 'input',
            name: 'frontWheelDiameter',
            message: 'Enter Front Wheel Diameter',
        },
        {
            type: 'input',
            name: 'frontWheelBrand',
            message: 'Enter Front Wheel Brand',
        },
        {
            type: 'input',
            name: 'rearWheelDiameter',
            message: 'Enter Rear Wheel Diameter',
        },
        {
            type: 'input',
            name: 'rearWheelBrand',
            message: 'Enter Rear Wheel Brand',
        },
    ]).then((answers) => {
        const motorbike = new Motorbike(
            Cli.generateVin(),
            answers.color,
            answers.make,
            answers.model,
            parseInt(answers.year),
            parseInt(answers.weight),
            parseInt(answers.topSpeed),
            [
                new Wheel(parseInt(answers.frontWheelDiameter), answers.frontWheelBrand),
                new Wheel(parseInt(answers.rearWheelDiameter), answers.rearWheelBrand),
            ]
        );
        this.vehicles.push(motorbike);
        this.selectedVehicleVin = motorbike.vin;
        this.performActions();
    });
}
```
### 7. Method to Perform Actions on Selected Vehicles
```typescript
performActions(): void {
    inquirer.prompt([
        {
            type: 'list',
            name: 'action',
            message: 'Select an action',
            choices: [
                'Print details',
                'Start vehicle',
                'Accelerate 5 MPH',
                'Decelerate 5 MPH',
                'Stop vehicle',
                'Turn right',
                'Turn left',
                'Reverse',
                'Tow a vehicle',
                'Do a wheelie',
                'Select or create another vehicle',
                'Exit',
            ],
        },
    ]).then((answers) => {
        for (let i = 0; i < this.vehicles.length; i++) {
            if ((this.vehicles[i] as any).vin === this.selectedVehicleVin) {
                const vehicle = this.vehicles[i];
                if (answers.action === 'Print details') {
                    vehicle.printDetails();
                } else if (answers.action === 'Start vehicle') {
                    vehicle.start();
                } else if (answers.action === 'Accelerate 5 MPH') {
                    vehicle.accelerate(5);
                } else if (answers.action === 'Decelerate 5 MPH') {
                    vehicle.decelerate(5);
                } else if (answers.action === 'Stop vehicle') {
                    vehicle.stop();
                } else if (answers.action === 'Turn right') {
                    vehicle.turn('right');
                } else if (answers.action === 'Turn left') {
                    vehicle.turn('left');
                } else if (answers.action === 'Reverse') {
                    vehicle.reverse();
                } else if (answers.action === 'Tow a vehicle' && vehicle instanceof Truck) {
                    this.findVehicleToTow(vehicle);
                    return;
                } else if (answers.action === 'Do a wheelie' && vehicle instanceof Motorbike) {
                    (vehicle as Motorbike).wheelie();
                } else if (answers.action === 'Select or create another vehicle') {
                    this.startCli();
                    return;
                } else if (answers.action === 'Exit') {
                    this.exit = true;
                }
            }
        }
        if (!this.exit) {
            this.performActions();
        }
    });
}
```
## 2. index.ts File
### Creating and Managing Vehicles
```typescript
// import classes
import Truck from "./classes/Truck.js";
import Car from "./classes/Car.js";
import Motorbike from "./classes/Motorbike.js";
import Wheel from "./classes/Wheel.js";
import Cli from "./classes/Cli.js";

// create an array of vehicles
const vehicles = [];

// Create instances of each vehicle type
const truck1 = new Truck(Cli.generateVin(), "red", "Ford", "F-150", 2021, 5000, 120, [], 10000);
const car1 = new Car(Cli.generateVin(), 'blue', 'Toyota', 'Camry', 2021, 3000, 130, []);
const motorbike1Wheels = [new Wheel(17, "Michelin"), new Wheel(17, "Michelin")];
const motorbike1 = new Motorbike(Cli.generateVin(), "black", "Harley Davidson", "Sportster", 2021, 500, 125, motorbike1Wheels);

// push vehicles to array
vehicles.push(truck1);
vehicles.push(car1);
vehicles.push(motorbike1);

// create a new instance of the Cli class
const cli = new Cli(vehicles);

// start the cli
cli.startCli();
```

## GitHub Repository
https://github.com/Moosorkh/vehiclevanguard

## Walkthrough Video
Watch the walkthrough video to see VehicleVanguard in action:
[VehicleVanguard walkthrough video](https://drive.google.com/file/d/1UWPhnSckxp6CE-aaexAopvEh1UUfCGK8/view)