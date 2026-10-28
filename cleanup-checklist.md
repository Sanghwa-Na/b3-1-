# 리소스 정리 체크리스트

> 실습 종료 후 서울 리전(ap-northeast-2)에서 순서대로 정리하고 체크하세요.

---

## 체크리스트

| 순서 | 리소스 | 확인 항목 | 상태 | 비고 |
|------|--------|-----------|------|------|
| 1 | **EC2 인스턴스** | `Terminated` 상태 확인 (Stop 아님) | [x] | `i-0babbe8xxxxxxxxxx` |
| 2 | **EBS 볼륨** | 미사용 볼륨 포함 모두 삭제 확인 | [x] | `Delete on termination` 확인 |
| 3 | **Elastic IP** | 할당된 EIP Release 확인 | [x] | 본 실습에서는 미할당 (확인만) |
| 4 | **Network Interface** | 잔여 ENI 삭제 확인 | [x] | EC2 종료 시 자동 정리됨 |
| 5 | **Security Group** | `aws-lab-web-sg` 삭제 확인 | [x] | `sg-0c7971xxxxxxxxxx` |
| 6 | **Route Table** | Subnet 연결 해제(Disassociate) 후 삭제 | [x] | `rtb-048fc9xxxxxxxxxx` |
| 7 | **Internet Gateway** | VPC에서 Detach 후 삭제 | [x] | `igw-0ad0e6xxxxxxxxxx` |
| 8 | **Subnet** | 삭제 확인 | [x] | `subnet-03a1aexxxxxxxxxxx` |
| 9 | **VPC** | 삭제 확인 (종속 리소스 없을 때) | [x] | `vpc-03a01xxxxxxxxxxxx` |
| 10 | **NAT Gateway** | 미생성 또는 삭제 확인 | [x] | 생성하지 않음 |
| 11 | **ELB / ALB** | 미생성 또는 삭제 확인 | [x] | 생성하지 않음 |
| 12 | **RDS** | 미생성 또는 삭제 확인 | [x] | 생성하지 않음 |
| 13 | **Billing 확인** | 사용량/요금 항목 확인 (청구 반영 지연 고려) | [x] | 사후 재확인 권장 |

---

## 확인 정보

| 항목 | 값 |
|------|-----|
| **확인일** | 2026-10-27 |
| **확인 리전** | ap-northeast-2 (Seoul) |
| **확인자** | sanghwa |

---

## 비고

- `Delete on termination` 설정이 꺼져 있으면 EC2 종료 후 EBS가 남을 수 있으니 볼륨 탭에서 반드시 확인
- 기본(Main) Route Table이나 기본 Security Group은 직접 삭제 불가할 수 있음 → VPC 삭제 과정에서 처리되는지 확인
- NAT Gateway, Load Balancer, RDS는 본 실습에서 생성하지 않았으므로 **미생성**으로 체크
- 청구 데이터 반영에는 지연이 있을 수 있으므로 정리 후에도 Billing Dashboard 재확인 권장