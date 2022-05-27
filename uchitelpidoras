#include <iostream>
#include <ctime>

using namespace std;

class Data {
public:
    int day;
    int month;
    int year;

    void setDate(int day_in, int month_in, int year_in) {
        day = day_in;
        month = month_in;
        year = year_in;
    }

    int monthcode() {
        switch (month)
        {
        case 1: case 10:
            return 1;
        case 5:
            return 2;
        case 8:
            return 3;
        case 2: case 3: case 11:
            return 4;
        case 6:
            return 5;
        case 12: case 9:
            return 6;
        case 4: case 7:
            return 0;
        }
    }

    int yearcode() {
        int firstcode;
        switch (year / 100)
        {
        case 19: case 23:
            firstcode = 0;
            break;
        case 20: case 24:
            firstcode = 6;
            break;
        case 21: case 25:
            firstcode = 4;
            break;
        }
        
        return (firstcode + year % 100 + (year % 100) / 4) % 7;
    }

    bool isLeap() {
        if (year % 4 == 0)
            return true;
        else
            return false;
    }

    Data plusdays(int days) {
        Data newdata;
        if (!isLeap()) {
            if (month == 12) {
                if (day + days > 31) {
                    newdata.setDate(day + days - 31, 1, year + 1);
                    return newdata;
                }
                else {
                    newdata.setDate(day + days, 12, year);
                    return newdata;
                }
            }
            else {
                if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10)
                    if (day + days > 31) {
                        newdata.setDate(day + days - 31, month + 1, year);
                        return newdata;
                    }
                    else {
                        newdata.setDate(day + days, month, year);
                        return newdata;
                    }
                if (month == 4 or month == 6 or month == 9 or month == 11)
                    if (day + days > 30) {
                        newdata.setDate(day + days - 30, month + 1, year);
                        return newdata;
                    }
                    else {
                        newdata.setDate(day + days, month, year);
                        return newdata;
                    }
                if (month == 2)
                    if (day + days > 28) {
                        newdata.setDate(day + days - 28, month + 1, year);
                        return newdata;
                    }
                    else {
                        newdata.setDate(day + days, month, year);
                        return newdata;
                    }
            }
        }
        else
            if (month == 12) {
                if (day + days > 31){
                    newdata.setDate(day + days - 31, 1, year + 1);
                    return newdata;
                }
                else {
                    newdata.setDate(day + days, 12, year);
                    return newdata;
                }
            }
            else {
                if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10)
                    if (day + days > 31) {
                        newdata.setDate(day + days - 31, month + 1, year);
                        return newdata;
                    }
                    else {
                        newdata.setDate(day + days, month, year);
                        return newdata;
                    }
                if (month == 4 or month == 6 or month == 9 or month == 11)
                    if (day + days > 30) {
                        newdata.setDate(day + days - 30, month + 1, year);
                        return newdata;
                    }
                    else {
                        newdata.setDate(day + days, month, year);
                        return newdata;
                    }
                if (month == 2)
                    if (day + days > 29) {
                        newdata.setDate(day + days - 29, month + 1, year);
                        return newdata;
                    }
                    else {
                        newdata.setDate(day + days, month, year);
                        return newdata;
                    }
            }
    }

    bool operator >(const Data &date1)
    {
        if (year > date1.year)
            return true;
        else
            if (year < date1.year)
                return false;
            else
                if (month > date1.month)
                    return true;
                else
                    if (month < date1.month)
                        return false;
                    else
                        if (day >= date1.day)
                            return true;
                        else
                            if (day < date1.day)
                                return false;
        
    }


    int weekday() {
        if (!isLeap())
            return (day + monthcode() + yearcode()) % 7;
        else
            if (month < 3)
                return (day + monthcode() + yearcode()) % 7 - 1;
            else
                return (day + monthcode() + yearcode()) % 7;
    }
};

int main(){
    setlocale(LC_ALL, "Russian");
    cout << "Введите две даты (формат : дд мм гггг)\n";
    int day, month, year;
    cin >> day >> month >> year;
    Data startData;
    startData.setDate(day, month, year);
    cin >> day >> month >> year;
    Data endData;
    endData.setDate(day, month, year);
    
    cout << "Введите нерабочие дни (пн - 2, вт - 3, ср - 4, чт - 5, пт - 6, сб - 0, вс - 1)\n";
    int weekend1, weekend2;
    cin >> weekend1 >> weekend2;

    double start = clock();

    int workcount = 0;
    Data helper = startData.plusdays(7);
    Data lastdata = startData;
    while (endData > helper) {
        workcount += 5;
        lastdata = helper;
        helper = helper.plusdays(7);
    }
    
    helper = lastdata;
    while (endData > helper) {
        if (helper.weekday() != weekend1 and helper.weekday() != weekend2)
            workcount += 1;
        helper = helper.plusdays(1);
    }

    double end = clock();
    double seconds = (double)(end - start) / (double) CLOCKS_PER_SEC;

    cout << workcount << "\n";
    printf("The time: %.5f seconds\n", seconds);

    return 0;
}
