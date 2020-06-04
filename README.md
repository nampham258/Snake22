#include <iostream>
using namespace std;

bool isPrime(int n)
{
	if (n == 2) return true;
	if (n <= 1) return false;
	else
	{
		for (int i = 2; i < n / 2; i++)
			if (n % i == 0)
				return false;
	}
	return true;
}

bool isPerfect(int n)
{
	int sum = 0;
	for (int i = 1; i < n; i++)
	{
		if (n % i == 0)
			sum += i;
	}
	if (sum == n)
		return true;
	else return false;
}

void NhapMang(int a[], int* N)
{
	cout << "Nhap so luong phan tu (<100): ";
	cin >> *N;
	cout << "Nhap mang: " << endl;
	for (int i = 0; i < *N; i++)
	{
		cout << "a[" << i << "]: ";
		cin >> a[i];
	}
}

void XuatMang(int a[], int* N)
{
	cout << "a[" << *N << "]: ";
	for (int i = 0; i < *N; i++)
		cout << a[i] << " ";
	cout << endl;
}
double TongN(int n)
{
	if (n == 0) return 0; 
	return n + TongN(n - 1);
}

double LuyThua(float x, int y)
{
	double P = 1;
	for (int i = 1; i <= y; i++)
		P*= x;
	return P;
}

long TichS1(int n)
{
	if (n == 0) return 0;
	else if (n == 1) return 1;
	return n * TichS1(n - 1);
}

double TongS2(int n)
{
	if (n == 0) return 1;
	return 1.0 / (2 * n + 1) + TongS2(n - 1);
}

double TongS3(int n)
{
	if (n == 0) return 1.0 / 2;
	return (2 * n + 1) / (2 * n + 2) + TongS3(n - 1);
}

double TongS4(float x, int n)
{
	if (n == 1) return x;
	else if (x == 0) return 0;
	else if (x == 1) return n;
	return LuyThua(x,n) + TongS4(x,n - 1);
}

double TongS5(float x, int n)
{
	if (n == 1) return x;
	if (x == 0) return 0;
	return (LuyThua(x, n)) / (TongN(n)) + TongS5(x, n - 1);
}

int CountPrime(int a[],int N, int& count)
{
	for (int i = N - 1; i >= 0; i--)
		if (!isPrime(a[i])) return CountPrime(a, i, count);
		else count++;
	return count;
}
int CountPerfect(int a[], int N, int& count)
{
	for (int i = N - 1; i >= 0; i--)
		if (!isPerfect(a[i])) return CountPrime(a, i, count);
		else count++;
	return count;
}
long TongChan(int a[], int N, int& count)
{
	for (int i = N - 1; i >= 0; i--)
		if (a[i] % 2 == 0) count += a[i];
		else return TongChan(a, i, count);
	return count;
}

int ListPrime(int a[], int N)
{
	for (int i = N - 1; i >= 0; i--)
		if (isPrime(a[i])) cout << i << " ";
		else ListPrime(a, i);
	cout << endl;
	return 0;
}

int main()
{
	float x = 0;
	int cases = -1, n = 0, N = 0, count = 0;
	int a[100];
	while (cases != 0)
	{
		cout << "-----------------------BAI TAP DE QUY-----------------------" << endl;
		cout << "(1) Nhap n va x cho cac cau (3) -> (7)" << endl;
		cout << "(2) Nhap mang so Nguyen Duong a[n] cho cac cau (8) -> (12) " << endl;
		cout << "(3) S(n) = 1 x 2 x 3 x ... x n" << endl;
		cout << "(4) S(n) = 1+(1/3) + (1/5) + ... + 1/(2n+1)" << endl;
		cout << "(5) S(n) = (1/2) + (3/4) + ... + ((2n+1)/(2n+2))" << endl;
		cout << "(6) S(n, x) = x + x^2 + x^3 + ... + x^n" << endl;
		cout << "(7) S(n, x) =  x + (x^2/(1 + 2)) + (x^3/(1 + 2 + 3)) + … + (x^n/(1 + 2 + … + n))" << endl;
		cout << "(8) Dem so Nguyen To trong mang 1 chieu cac so nguyen duong." << endl;
		cout << "(9) Dem so Hoan Thien trong mang 1 chieu cac so nguyen duong." << endl;
		cout << "(10)Tinh tong cac so chan trong mang 1 chieu cac so nguyen duong." << endl;
		cout << "(11)Liet ke cac vi tri cua phan tu Nguyen to trong mang 1 chieu cac so nguyen duong" << endl;
		cout << "(12)Liet ke cac vi tri cua phan tu So Chan trong mang 1 chieu cac so nguyen duong." << endl;
		cout << "(13)Tinh tong cac gia tri Lon Hon Gia tri Dung Lien Truoc No trong mang 1 chieu cac so thuc." << endl;
		cout << "(14)Dem phan biet cac gia tri trong mang 1 chieu." << endl;
		cout << "(0) Thoat chuong trinh." << endl;
		cout << "Nhap lua chon: ";
		cin >> cases;
		cout << "-------------------------------------------------------------" << endl;
		switch (cases)
		{
		case 1: 
		{
			cout << "Nhap n nguyen: ";
			cin >> n;
			cout << "Nhap x: ";
			cin >> x;
			break;
		}
		case 2:
		{
			NhapMang(a, &N);
			break;
		}
		case 3:cout << "n = " << n << endl; cout << "S(" << n << ") = " << TichS1(n) << endl; break;
		case 4:cout << "n = " << n << endl; cout << "S(" << n << ") = " << TongS2(n) << endl; break;
		case 5:cout << "n = " << n << endl; cout << "S(" << n << ") = " << TongS3(n) << endl; break;
		case 6:cout << "n = " << n << endl; cout << "x = " << x << endl; cout << "S(" << n << ", " << x << ") = " << TongS4(x, n) << endl; break;
		case 7:cout << "n = " << n << endl; cout << "x = " << x << endl; cout << "S(" << n << ", " << x << ") = " << TongS5(x, n) << endl; break;
		case 8: XuatMang(a, &N); cout << "So luong so Nguyen To trong mang vua nhap: " << CountPrime(a, N, count) << endl; count = 0; break;
		case 9: XuatMang(a, &N); cout << "So luong so Hoan Thien trong mang vua nhap: " << CountPerfect(a, N, count) << endl; count = 0; break;
		case 10:XuatMang(a, &N); cout << "Tong cac so chan trong mang vua nhap: " << TongChan(a, N, count) << endl; break;
		case 11:XuatMang(a, &N); cout << "Vi tri cac so Nguyen To trong mang vua nhap: "; ListPrime(a, N); break;
		case 0: return 1;
		}
		system("pause");
		system("cls");
	}
}
