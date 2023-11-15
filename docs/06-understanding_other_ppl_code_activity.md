# Understanding Unfamiliar Code - Hands-On Exercise 

Now it's your turn to try! 


## The Code

Let's say you were handed this bit of code to work with (and eventually modify), but first you need to figure out what's going on with it. Unfortunately, the original programmer left very little in the way of notes or annotation.

**Note**: This code is just an example and was written strictly for educational purposes.

```
use ode_solvers::{Euler, OdeMethod};
use plotters::prelude::*;
use std::fs::File;


const N: f64 = 1000000.0;  
const I0: f64 = 10.0;  
const R0: f64 = 0.0;   
const S0: f64 = N - I0 - R0;  
const BETA: f64 = 0.3;  
const GAMMA: f64 = 0.1;  

fn sir_model(t: f64, y: &[f64], v: f64) -> Vec<f64> {
    let s = y[0];
    let i = y[1];
    let r = y[2];
    let dsdt = -BETA * s * i / N - v * s;
    let didt = BETA * s * i / N - GAMMA * i;
    let drdt = GAMMA * i + v * s;
    vec![dsdt, didt, drdt]
}

fn main() {

    let mut solver = Euler::new(sir_model);
    solver.set_initial_condition(&[S0, I0, R0]);


    let root = BitMapBackend::new("sir_vaccination.png", (800, 600)).into_drawing_area();
    root.fill(&WHITE).unwrap();
    let mut chart = ChartBuilder::on(&root)
        .caption("SIR model with vaccination", ("sans-serif", 40))
        .set_label_area_size(LabelAreaPosition::Left, 60)
        .set_label_area_size(LabelAreaPosition::Bottom, 40)
        .build_cartesian_2d(0.0..100.0, 0.0..N)
        .unwrap();

    let mut data1 = vec![];
    for _ in 0..1000 {
        let y = solver.integrate(0.1, 0.0);
        data1.push((solver.time(), y[0], y[1], y[2]));
    }


    let vac_rate = 0.1;   
    let vac_coverage = 0.5;   
    let vac_num = vac_coverage * N;   
    let mut data2 = vec![];
    for i in 0..1000 {
        let t = i as f64 * 0.1;
        let v = if t >= 50.0 && t < 150.0 {vac_num * vac_rate} else {0.0};
        let y = solver.integrate(0.1, v);
        data2.push((solver.time(), y[0], y[1], y[2]));
    }


    chart
        .configure_mesh()
        .x_labels(10)
        .y_labels(10)
        .disable_x_mesh()
        .disable_y_mesh()
        .draw()
        .unwrap();
    chart
        .draw_series(LineSeries::new(
            data1.iter().map(|d|
```

## Questions

1. Write a query that identifies the features that can be used to determine the coding language, as well as the version of the language. What language and version is it written in? What features give away the coding language?

1. Create a prompt that determines what this code does, as well as important features of the program. What does this code do?

1. Write a prompt that determines the purpose of this specific code snippet:

```
 let root = BitMapBackend::new("sir_vaccination.png", (800, 600)).into_drawing_area();
```
What is the purpose of this line of code?


