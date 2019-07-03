# Exponential growth with IaC superpowers

Talk performed by myself and [Tommaso Previero](https://github.com/eltomato) at Agile Venture Vimercate 2019

*Video*:

*Slides*: [Slideshare](https://www.slideshare.net/CarloCorti5/superpoteri-e-crescita-esponenziale-dellorganizzazione-con-ia-c-agile-venture-vimercate-2019)

*Demo*: Code available in this repository

*Terraform script*:
```terraform
resource "google_bigquery_dataset" "auditing-dataset" {
  dataset_id = "auditing"
  location = "EU"
}

resource "google_bigquery_table" "APPLICATION_LOGS" {
  dataset_id = "${google_bigquery_dataset.auditing-dataset.dataset_id}"
  table_id = "APPLICATION_LOGS"

  time_partitioning {
    type = "DAY"
    expiration_ms = 1209600000
  }
}
``` 
