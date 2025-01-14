### Шанс вопроса: 13%

Провайдеры в Terraform — это компоненты, которые позволяют взаимодействовать с различными облачными платформами или поставщиками услуг. Они предоставляют интерфейс для создания, обновления и удаления ресурсов в рамках определенного провайдера. Провайдеры являются основой для всех конфигураций Terraform и позволяют управлять различными облаками (например, AWS, Google Cloud, Azure) или локальными инфраструктурами.

Пример использования провайдера для AWS:

```hcl
provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "terraform-example"
  }
}
```

В этом примере мы используем провайдера AWS для создания виртуальной машины (EC2) в регионе us-west-2.