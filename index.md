//+-------------------------------------------------------------------------------+
//| Experts Advisor.mq4 
//| Copyright 2021 | asrafnasri, All rights reserved.
//| https://asrafnasriofficial.blogspot.com
//+-------------------------------------------------------------------------------+
#property copyright "company name"
#property link "Link to the company website"
#property version "program version, maximum 31 characters"
#property discription "the total lenght of all description can not exceed 511 characters including line feed"
#property strict
//+------------------------------------------------------------------+
//| Expert add function
//+------------------------------------------------------------------+
datetime currentBar = 0;
int logFileHandle = INVALID_HANDLE;

datetime lastActBuy = 0;

input bool DebugMode = false; //Write strategy actions to logs
input bool WriteDebugLogToFile = false;
//+------------------------------------------------------------------+
//| Expert initialization function
//+------------------------------------------------------------------+
void OnInit()
{
   if(DebugMode && WriteDebugLogToFile)
     logFileHandle = FileOpen(StringConcatenate(MathRand(), "-vsb.log"), FILE_WRITE|FILE_TXT|FILE_SHARE_READ);
}
//+------------------------------------------------------------------+
//| Expert deinitialization function
//+------------------------------------------------------------------+
void OnDeinit(const int reason)
{
   if(logFileHandle != INVALID_HANDLE)
     FileClose(logFileHandle);
}

void WriteDebugLog(string logMessage)
{
   Print(logMessage);
   if (logFileHandle != INVALID_HANDLE && WriteDebugLogToFile)
     FileWriteString(logFileHandle, StringConcatenate(TimeToStr(TimeCurrent(),TIME_DATE|TIME_SECONDS), " " ,logMessage, "\r\n"));
  }
//+------------------------------------------------------------------+
//| Expert tick function
//+------------------------------------------------------------------+
void OnTick()
  {
  	
  }
//+------------------------------------------------------------------+
