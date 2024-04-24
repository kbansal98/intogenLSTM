# intogenLSTM
A Pytorch based,  custom LSTM network and dataset for predicting the consequences of cancerous mutations using the nearest prior mutation sequences. Based on a subset of the intogen somatic tumor mutation database: https://www.intogen.org/search

## Network Architecture
![](https://github.com/kbansal98/intogenLSTM/blob/main/modelJPG.jpg)

## Original Dataset Statistics
| Information     | Value        |
|-----------------|--------------|
| Cancer types    | 73           |
| Cohorts         | 266          |
| Samples         | 33,019       |
| Mutations       | 252,486,809  |
| Driver genes    | 619          |

### Visualization of Driver Gene Distribution
![From intogen](https://github.com/kbansal98/intogenLSTM/blob/main/intogenGRaph.jpg)

<table>
  <tr>
    <td style="padding-right: 100px;">
      <h2>Dataset Statistics</h2>
      <table>
        <tr>
          <th>Statistic</th>
          <th>Value</th>
        </tr>
        <tr>
          <td>Number of triplets</td>
          <td>1440</td>
        </tr>
        <tr>
          <td>Number of mutations</td>
          <td>5760</td>
        </tr>
        <tr>
          <td>Number of unique mutation sequences</td>
          <td>161</td>
        </tr>
        <tr>
          <td>Number of unique chromosomes</td>
          <td>2</td>
        </tr>
        <tr>
          <td>Number of unique consequences</td>
          <td>7</td>
        </tr>
      </table>
    </td>
<td style="padding-left: 100px;">
  <h2>Consequence Frequencies</h2>
  <table>
    <tr>
      <th>Consequence</th>
      <th>Frequency</th>
    </tr>
    <tr>
      <td>missense_variant</td>
      <td style="background-color: #f0f0f0">653</td>
    </tr>
    <tr>
      <td>frameshift_variant</td>
      <td style="background-color: #f0f0f0">317</td>
    </tr>
    <tr>
      <td>splice_acceptor_variant</td>
      <td style="background-color: #f0f0f0">36</td>
    </tr>
    <tr>
      <td>splice_donor_variant</td>
      <td style="background-color: #f0f0f0">13</td>
    </tr>
    <tr>
      <td>synonymous_variant</td>
      <td style="background-color: #f0f0f0">150</td>
    </tr>
    <tr>
      <td>inframe_deletion</td>
      <td style="background-color: #f0f0f0">55</td>
    </tr>
    <tr>
      <td>Stop_Gained</td>
      <td style="background-color: #f0f0f0">216</td>
    </tr>
  </table>
</td>
    
# Downloading and Using Dataset
The PKL file of pre-packaged triplets can be accessed at: https://drive.google.com/file/d/1-7LimJXEkoHPl58hKYj9VD3iBhO3HePR/view?usp=drive_link. You can also go to the original intogen dataset (linked above), and use processTSV and/or makeTriplets in order to create your own datasets of mutations.

## Preprocessing Training Data

To preprocess the raw data from the intogen website (for driver genes not in the given training data), follow these steps:

1. Set the `folder_path` variable to the path where your TSV files are located.
2. Define the `consequence_mapping` dictionary to map consequence types to numerical representations.
3. Specify the `max_mutation_length` variable to match the length of the maximum insertion/deletion sequence in your data.
4. Iterate through all files in the folder, process each TSV file using the `process_tsv` function, and save the processed DataFrame as a Pickle file for training.

```python
import os
import pickle

# Define the folder path containing the TSV files
folder_path = "/content/drive/MyDrive/NLP_DNA_TrainingData/"

# Define the known consequence types and their numerical representations
consequence_mapping = {
   'missense_variant': 0,
    'stop_gained': 1,
    'frameshift_variant': 2,
    'splice_acceptor_variant': 3,
    'splice_donor_variant': 4,
    'synonymous_variant': 5,
    'inframe_deletion': 6,
}

# Define the maximum mutation sequence length
max_mutation_length = 20  

# Iterate through all files in the folder
for file_name in os.listdir(folder_path):
    if file_name.endswith(".tsv"):
        file_path = os.path.join(folder_path, file_name)
        # Process the TSV file
        processed_df = process_tsv(file_path)

        # Save the processed DataFrame as a Pickle file for training
        output_file_path = os.path.join("/content/drive/MyDrive/NLP_DNA_PKLs", f"{file_name[:-4]}.pkl")
        with open(output_file_path, 'wb') as f:
            pickle.dump(processed_df, f)


