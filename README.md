/*Вывести на дисплей календарь на выбранный месяц
с учетом указанного номера дня недели для начала
месяца.*/
#include <iostream>
using namespace std;
int main()
{
	setlocale(LC_ALL, "rus");
	int num_of_days, dn, month, count = 0;
	bool marker = false, reset = false;

	cout << "Введите номер месяца ";
	cin >> month;
	cin.ignore(32767, '\n');
	if (!(month >= 1 && month <= 12))
	{
		cout << "Вы ошиблись при вводе месяца " << endl; return 0;
	}

	cout << "Введите номер дня начала месяца ";
	cin >> dn;
	cin.ignore(32767, '\n');
	if (!(dn >= 1 && dn <= 7)) 
	{
		cout << "Вы ошиблись при вводе дня начала месяца " << endl; return 0;
	}
	


	if (month == 1 || month == 3 || month == 5 || month == 7 || month == 8 || month == 10 || month == 12)
		num_of_days = 31;
	else if (month == 4 || month == 6 || month == 9 || month == 11)
	{
		num_of_days = 30;
	}
	else if (month == 2)
	{
		num_of_days = 28;
	}
	else
	{
		cout << "Некоректный номер месяца" << endl;
	}

	cout << "\t\t\t Месяц номер " << month << endl;
	cout << "\tПн\tВт\tСр\tЧт\tПт\tСб\tВс\n" << endl;
	int a = 0;
	while (true)
	{
		cout << "\t";
		for (int i = 1; i <= 7; i++)
		{
			if (i == dn)
			{
				marker = true;
			}
			if (marker)
			{
				count++;
				cout << count << "\t";
				if (count == num_of_days)
				{
					reset = true;
					break;
				}
			}
			else
			{
				cout << "\t";
			}

		}
		cout << "\n";
		if (reset)
			break;
	}

	return 0;
}
