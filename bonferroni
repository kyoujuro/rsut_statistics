use std::env;

fn bonferroni_correction(p_values: &Vec<f64>, num_comparisons: usize) -> Vec<f64> {
    p_values.iter().map(|&p| p * (num_comparisons as f64)).collect()
}

fn main() {
    let args: Vec<String> = env::args().collect();
    let p_values: Result<Vec<f64>, _> = args[1..].iter().map(|x| x.parse()).collect();

    match p_values {
        Ok(p_values) => {
            let num_comparisons = p_values.len();
            let corrected_p_values = bonferroni_correction(&p_values, num_comparisons);
            println!("{:?}", corrected_p_values);
        }
        Err(_) => {
            eprintln!("Error: Invalid input. Please provide a list of p-values as arguments.");
            std::process::exit(1);
        }
    }
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_bonferroni_correction() {
        let p_values = vec![0.01, 0.02, 0.03, 0.04, 0.05];
        let num_comparisons = p_values.len();
        let corrected_p_values = bonferroni_correction(&p_values, num_comparisons);
        assert_eq!(corrected_p_values, vec![0.05, 0.1, 0.15, 0.2, 0.25]);
    }
}
