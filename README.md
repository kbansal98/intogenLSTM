# intogenLSTM
An LSTM network and dataset for predicting the consequences of cancerous mutations using prior mutation equences.



## Dataset Statistics


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


## Consequence Frequencies
<table>
  <tr>
    <th>Consequence</th>
    <th>Frequency</th>
  </tr>
  <tr>
    <td>0</td>
    <td style="background-color: #f0f0f0">653</td>
  </tr>
  <tr>
    <td>2</td>
    <td style="background-color: #f0f0f0">317</td>
  </tr>
  <tr>
    <td>3</td>
    <td style="background-color: #f0f0f0">36</td>
  </tr>
  <tr>
    <td>4</td>
    <td style="background-color: #f0f0f0">13</td>
  </tr>
  <tr>
    <td>5</td>
    <td style="background-color: #f0f0f0">150</td>
  </tr>
  <tr>
    <td>6</td>
    <td style="background-color: #f0f0f0">55</td>
  </tr>
  <tr>
    <td>7</td>
    <td style="background-color: #f0f0f0">216</td>
  </tr>
</table>





## Original Dataset Statistics
| Information     | Value        |
|-----------------|--------------|
| Cancer types    | 73           |
| Cohorts         | 266          |
| Samples         | 33,019       |
| Mutations       | 252,486,809  |
| Driver genes    | 619          |
